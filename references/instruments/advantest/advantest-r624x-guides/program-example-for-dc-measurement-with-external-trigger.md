# Program example for DC measurement (with external trigger)

Measurement characteristics:

Function: VSIM - Source voltage and measure current.
Source voltage: 10 V.
Base voltage: 1 V.
Current compliance: 0.5 A.
Pulse width: 5 ms. Pulse period: 10 ms.
Measurement delay time: 1 ms. Integration time: 1 ms. Response: Fast.

After operation starts, pulse an external trigger input signal to measure the channel operation register. Then read the fixed end bit, capture the measurement data, and print the result.

```python
from pymeasure.instruments.advantest.advantestR624X import AdvantestR6246, COR, CurrentRange, SRER, SampleHold, SampleMode, TriggerInputType, VoltageRange

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
