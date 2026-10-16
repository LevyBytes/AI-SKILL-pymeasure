# pymeasure.instruments.ni.virtualbench.VirtualBench.MixedSignalOscilloscope.configure_timing

[Owning MixedSignalOscilloscope contract](overview.md)

configure_timing(*sample_rate*, *acquisition_time*, *pretrigger_time*, *sampling_mode*)

Set MSO timing settings

Parameters:

- **sample_rate** (*int*) – Sample rate (15.26kS - 1GS)

- **acquisition_time** (*float*) – Acquisition time (1ns - 68.711s)

- **pretrigger_time** (*float*) – Pretrigger time (0s - 10s)

- **sampling_mode** — Sampling mode selection (`'SAMPLE'` or `'PEAK_DETECT'`)
