# pymeasure.instruments.ni.virtualbench.VirtualBench.MixedSignalOscilloscope.configure_analog_edge_trigger

[Owning MixedSignalOscilloscope contract](overview.md)

configure_analog_edge_trigger(*trigger_source*, *trigger_slope*, *trigger_level*, *trigger_hysteresis*, *trigger_instance*)

Sets a trigger on the specified source that fires when the analog edge reaches the specified levels.

Parameters:

- **trigger_source** (*str*) – Channel string

- **trigger_slope** (*int** or **str*) — Trigger slope selection (`'RISING'`, `'FALLING'` or `'EITHER'`)

- **trigger_level** (*float*) – Trigger level

- **trigger_hysteresis** (*float*) – Trigger hysteresis

- **trigger_instance** (*int** or **str*) — Trigger instance
