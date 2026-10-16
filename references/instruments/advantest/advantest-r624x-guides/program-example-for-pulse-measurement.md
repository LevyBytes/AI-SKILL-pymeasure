# Program example for pulse measurement

Measurement characteristics:

Function: ISVM - Source current and measure voltage.
Pulse generation current: 100mA. Base current: 1mA. Voltage compliance: 5V.
Pulse width: 0. Pulse period: 0.
Measurement delay time: 0. Integration time: 1ms. Response: Fast.

After the operation starts, repeat the measurement 10 times with the trigger command and print the measurement results.

```python
from pymeasure.instruments.advantest.advantestR624X import AdvantestR6246, COR, CurrentRange, SampleHold, SampleMode, VoltageRange

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
