# Fixed Level Sweep Program Example

Measurement characteristics:

Function: VSVM - Voltage source and voltage measurement.
Level value: 15V. Bias value: 0V. Number of measurements: 20 times.
Compliance: 6mA. Measuring range: Best fixed range (=60V range).
Integration time: 100us. Measurement delay time: 0. Hold time: 1ms.
Sampling mode: automatic sweep.
Measurement data output method: Buffering output (output of specified data).

After operation starts, make 20 measurements in fixed sweep. Detect sweep completion by checking the Channel Operation Register (COR). After the sweep is finished, read measured data from 1 to 2 using the RMM command.

```python
from pymeasure.instruments.advantest.advantestR624X import AdvantestR6246, COR, MeasurementType, OutputType, SampleHold, SampleMode, TriggerInputType, VoltageRange

smu = AdvantestR6246("GPIB::1")

# First we setup our main parameters
smu.reset()                                                      # Set default parameters

smu.ch_A.set_output_type(output_type = OutputType.BUFFERING_OUTPUT_SPECIFIED,
                     measurement_type = MeasurementType.MEASURE_DATA)

smu.set_output_format(delimiter_format = 2,                           # No header, ASCII format
                  block_delimiter = 1,                           # Make it the same as the terminator
                  terminator = 1)                                # CR, LF<EOI>

smu.ch_A.analog_input = 1                                        # Turn off the analog input.

smu.set_lo_common_connection_relay(enable = True)                               # Turns the connection relay on

smu.ch_A.set_wire_mode(four_wire = False,                             # disable four wire measurements
                   lo_guard = True)                              # enable the LO-GUARD relay.

smu.ch_A.auto_zero_enabled = False
smu.ch_A.trigger_input = TriggerInputType.ALL                    # Mode 1 enables the trigger input signal

# Now we set measurement specific variables
smu.ch_A.clear_measurement_buffer()
smu.ch_A.set_sample_mode(SampleMode.ASYNC, auto_sampling = True)
smu.ch_A.voltage_fixed_level_sweep(voltage_range = VoltageRange.FIXED_60V,
                                   voltage_level = 15,
                                   measurement_count = 20,       # 20 measurements
                                   current_compliance = 6E-3,    # compliance at 6mA
                                   bias = 0)
smu.ch_A.measure_voltage(voltage_range = VoltageRange.FIXED_BEST)
smu.ch_A.sample_hold_mode = SampleHold.MODE_100uS
smu.ch_A.set_timing_parameters(hold_time = 1E-3,                 # 1ms sec hold time
                               measurement_delay = 0,            # 0 sec delay between measurements
                               pulsed_width = 0,                 # 0 sec pulse width
                               pulsed_period = 0)                # 0 sec pulse period

smu.ch_A.enable_source()                                         # Set channel in operating state
smu.ch_A.trigger()                                               # Start the sweep

while not smu.ch_A.operation_register & COR.END_OF_SWEEP:        # Wait until the sweep is done
    pass

# Read measurements
for i in range(1, 20):
    measurement = smu.ch_A.read_measurement_from_addr(i)
    print(i, measurement)

smu.ch_A.standby()                                               # Put channel A in standby mode

```
