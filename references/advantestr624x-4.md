# Advantestr624X (part 4)

> Pymeasure reference. Original prose; identifiers preserved verbatim.

### Program example for DC measurement (with external trigger)

Measurement characteristics:

Function: VSIM - Source voltage and measure current.
Source voltage: 10 V.
Base voltage: 1 V.
Current compliance: 0.5 A.
Pulse width: 5 ms. Pulse period: 10 ms.
Measurement delay time: 1 ms. Integration time: 1 ms. Response: Fast.

After operation starts, pulse an external trigger input signal to measure the channel operation register. Then read the fixed end bit, capture the measurement data, and print the result.

```python
smu = AdvantestR6246("GPIB::1")
smu.reset()                                                      # Set default parameters

smu.ch_A.auto_zero_enabled = False
smu.ch_A.set_sample_mode(SampleMode.ASYNC, False)                     # Asynchronous operation and single shot sampling by trigger and command
smu.ch_A.voltage_pulsed_source(
      source_range = VoltageRange.FIXED_BEST,
      pulse_value = 10,
      base_value = 1,
      current_compliance = 0.5)
smu.ch_A.measure_current(current_range=CurrentRange.FIXED_BEST)  # Fixed range required for pulsed
smu.ch_A.fast_mode_enabled = True                                # Set channel response to fast
smu.ch_A.sample_hold_mode = SampleHold.MODE_1mS                  # Sample at 1mS
smu.ch_A.set_timing_parameters(hold_time = 0,                    # 0 sec hold time
                               measurement_delay = 1E-3,         # 1ms delay between measurements
                               pulsed_width = 5E-3,              # 5ms pulse width
                               pulsed_period = 10E-3)            # 10ms pulse period
smu.ch_A.trigger_input = TriggerInputType.ALL                    # Mode 1 enables the trigger input signal
smu.ch_A.output_enable_register = COR.HAS_MEASUREMENT_DATA       # Measurement data available
smu.service_request_enable_register = SRER.COP                   # COP Set when a bit in the Channel Operations Register is set with the Enable Register set to Enable.
smu.ch_A.enable_source()                                         # Set channel in operating state
smu.ch_A.select_for_output()                                     # Select channel for measurement output

for i in range(1, 10):
    while not smu.ch_A.operation_register & COR.HAS_MEASUREMENT_DATA:
        pass

    measurement = smu.read_measurement()
    print(f"NO {i} {measurement}")

    while not smu.ch_A.operation_register & COR.WAITING_FOR_TRIGGER:
        pass

smu.ch_A.standby()                                               # Put channel A in standby mode

```

### Program example for pulse measurement

Measurement characteristics:

Function: ISVM - Source current and measure voltage.
Pulse generation current: 100mA. Base current: 1mA. Voltage compliance: 5V.
Pulse width: 0. Pulse period: 0.
Measurement delay time: 0. Integration time: 1ms. Response: Fast.

After the operation starts, repeat the measurement 10 times with the trigger command and print the measurement results.

```python
smu = AdvantestR6246("GPIB::1")
smu.reset()                                                         # Set default parameters
smu.ch_A.set_sample_mode(SampleMode.ASYNC, auto_sampling = False)
smu.ch_A.current_pulsed_source(
      source_range = CurrentRange.FIXED_600mA,
      pulse_value = 0.1,                                            # 100mA
      base_value = 1E-3,                                            # 1mA
      voltage_compliance = 5)                                       # 5V
smu.ch_A.measure_voltage(voltage_range = VoltageRange.FIXED_BEST)
smu.ch_A.fast_mode_enabled = True                                   # Set channel response to fast
smu.ch_A.sample_hold_mode = SampleHold.MODE_1mS                     # Sample at 1mS
smu.ch_A.set_timing_parameters(hold_time = 0,                       # 0 sec hold time
                               measurement_delay = 0,               # 0 sec delay between measurements
                               pulsed_width = 0,                    # 0 sec pulse width
                               pulsed_period = 0)                   # 0 sec pulse period
smu.ch_A.enable_source()                                            # Set channel in operating state
smu.ch_A.select_for_output()                                        # Select channel for measurement output

for i in range(1, 10):
    smu.ch_A.trigger()                                              # Trigger measurement

    measurement = smu.read_measurement()
    print(f"NO {i} {measurement}")

    while not smu.ch_A.operation_register & COR.WAITING_FOR_TRIGGER:
        pass

smu.ch_A.standby()                                                  # Put channel A in standby mode

```

### Fixed Level Sweep Program Example

Measurement characteristics:

Function: VSVM - Voltage source and voltage measurement.
Level value: 15V. Bias value: 0V. Number of measurements: 20 times.
Compliance: 6mA. Measuring range: Best fixed range (=60V range).
Integration time: 100us. Measurement delay time: 0. Hold time: 1ms.
Sampling mode: automatic sweep.
Measurement data output method: Buffering output (output of specified data).

After operation starts, make 20 measurements in fixed sweep. Detect sweep completion by checking the Channel Operation Register (COR). After the sweep is finished, read measured data from 1 to 2 using the RMM command.

```python
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
