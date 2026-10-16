# Simple dual channel synchronous measurement example

[Owning PyMeasure class, adapter and connection contract](../advantest-r624x-sequence-wait-mode/overview.md)

Measurement characteristics:

Channel A (MASTER) uses DC voltage source + current measurement. Channel B (SLAVE) uses Pulsed voltage source + current measurement.

Note

For dual-channel synchronous mode (`PULSED_SYNC`), set `auto_sampling=False` when calling `sample_mode()`. If `auto_sampling=True` is used (the default), the automatically output data reports the generated/source value rather than the measurement result.

Warning

`CurrentRange.AUTO` and `AUTO_*` (limited auto) ranges are invalid for pulse measurement or pulse sweep; the instrument reports error 00211. Configure pulsed modes with a fixed range such as `CurrentRange.FIXED_BEST`.

```python
from pymeasure.instruments.advantest.advantestR624X import AdvantestR6246, CurrentRange, SampleHold, SampleMode, VoltageRange

smu = AdvantestR6246("GPIB::1")
smu.reset()                                               # Set default parameters

# Ch A (MASTER): DC voltage source + current measurement
smu.ch_A.voltage_source(source_range=VoltageRange.FIXED_6V,
                        source_value=5,
                        current_compliance=2)
smu.ch_A.measure_current(current_range=CurrentRange.FIXED_BEST)

# Ch B (SLAVE): Pulsed voltage source + current measurement
smu.ch_B.fast_mode_enabled = True
smu.ch_B.sample_hold_mode = SampleHold.MODE_1mS
smu.ch_B.voltage_pulsed_source(source_range=VoltageRange.FIXED_6V,
                               pulse_value=6, base_value=0,
                               current_compliance=2)
smu.ch_B.measure_current(current_range=CurrentRange.FIXED_BEST)
smu.ch_B.set_timing_parameters(hold_time=0, measurement_delay=1e-4,
                           pulsed_width=1e-2, pulsed_period=2e-2)

# PULSED_SYNC with auto_sampling=False (critical for correct readout)
smu.ch_A.set_sample_mode(SampleMode.PULSED_SYNC, auto_sampling=False)

smu.ch_A.enable_source()
smu.ch_B.enable_source()

for i in range(10):
    smu.ch_A.select_for_output()                          # Select channel A (FCH 01?)
    smu.ch_A.trigger()                                    # Trigger (XE 1, syncs both)
    Ic_a = smu.read_measurement()                         # Read channel A measurement

    smu.ch_B.select_for_output()                          # Select channel B (FCH 02?)
    Ic_b = smu.read_measurement()                         # Read channel B measurement
    print(f'Ic_a={Ic_a}, Ic_b={Ic_b}')

smu.standby()                                             # Put channel A & B in standby

```
