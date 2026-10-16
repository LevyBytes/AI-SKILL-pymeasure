# pymeasure.instruments.ni.virtualbench.VirtualBench.FunctionGenerator.configure_arbitrary_waveform_gain_and_offset

[Owning FunctionGenerator contract](overview.md)

configure_arbitrary_waveform_gain_and_offset(*gain*, *dc_offset*)

Sets arbitrary waveform output with the requested gain and offset. If output is already active, it begins after the current waveform ends; otherwise it begins when output is enabled.

Parameters:

- **gain** (*float*) — Gain multiplier applied to waveform values

- **dc_offset** (*float*) — DC offset value in volts
