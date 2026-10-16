# pymeasure.instruments.ni.virtualbench.VirtualBench.FunctionGenerator.configure_arbitrary_waveform

[Owning FunctionGenerator contract](overview.md)

configure_arbitrary_waveform(*waveform*, *sample_period*)

Sets the instrument to generate a waveform. When output is already enabled, the new waveform follows the current one; otherwise it starts as soon as output is enabled.

Parameters:

- **waveform** (*list*) — Waveform represented as a list of values

- **sample_period** (*float*) — Time spacing between waveform points (maximum of 125MS/s, which equals 80ns)
