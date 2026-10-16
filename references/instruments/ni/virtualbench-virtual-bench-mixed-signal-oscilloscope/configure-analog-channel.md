# pymeasure.instruments.ni.virtualbench.VirtualBench.MixedSignalOscilloscope.configure_analog_channel

[Owning MixedSignalOscilloscope contract](overview.md)

configure_analog_channel(*channel*, *enable_channel*, *vertical_range*, *vertical_offset*, *probe_attenuation*, *vertical_coupling*)

Configure analog measurement channel

Parameters:

- **channel** (*str*) – Channel string

- **enable_channel** (*bool*) – Enable/Disable channel

- **vertical_range** (*float*) — Vertical measurement range (0V - 20V); the instrument snaps to `[20, 10, 5, 2, 1, 0.5, 0.2, 0.1, 0.05]`, with each entry equal to 5x the value displayed in the native UI.

- **vertical_offset** (*float*) — Vertical offset correction (inverted compared to VB native UI, -20V - +20V, resolution 0.1mV)

- **probe_attenuation** (*int** or **str*) — Probe attenuation choice (`'ATTENUATION_10X'` or `'ATTENUATION_1X'`)

- **vertical_coupling** (*int** or **str*) — Vertical coupling choice (`'AC'` or `'DC'`)
