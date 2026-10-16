# Program example for DC measurement

[Owning PyMeasure class, adapter and connection contract](../advantest-r624x-sequence-wait-mode/overview.md)

Measurement characteristics:

Function: VSIM - voltage-source/current-measure operation. Trigger voltage is 10V. Current compliance is 0.5A. Measurement delay time is 1ms. Integration time is 1 PLC. Response is Fast.

After operation starts, a trigger command repeats the measurement 10 times, and the results are printed.

```python
from pymeasure.instruments.advantest.advantestR624X import AdvantestR6246, SampleHold, SampleMode, VoltageRange

smu = AdvantestR6246("GPIB::1")
smu.reset()                                                      # Set default parameters
smu.ch_A.set_sample_mode(SampleMode.ASYNC, False)                     # Asynchronous operation and single shot sampling by trigger and command
smu.ch_A.voltage_source(source_range = VoltageRange.FIXED_BEST,
                        source_value = 10,
                        current_compliance = 0.5)                # compliance of 0.5A
smu.ch_A.measure_current()                                       # Measure current
smu.ch_A.set_timing_parameters(hold_time = 0,                    # 0 sec hold time
                               measurement_delay = 1E-3,         # 1ms delay between measurements
                               pulsed_width = 5E-3,              # 5ms pulse width
                               pulsed_period = 10E-3)            # 10ms pulse period
smu.ch_A.sample_hold_mode = SampleHold.MODE_1PLC                 # Sample at 1 power line cycle
smu.ch_A.fast_mode_enabled = True                                # Set channel response to fast
smu.ch_A.enable_source()                                         # Set channel in operating state
smu.ch_A.select_for_output()                                     # Select channel for measurement output

for i in range(1, 10):
    smu.ch_A.trigger()                                           # Trigger a measurement
    measurement = smu.read_measurement()
    print(f"NO {i} {measurement}")

smu.ch_A.standby()                                               # Put channel A in standby mode

```
