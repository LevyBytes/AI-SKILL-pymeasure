# pymeasure.instruments.agilent.Agilent33220A.pulse_period

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *pulse_period*: Any*

Set pulse waveform period in seconds (float, strict from 200e-9 to 2e3). The period replaces frequency for all waveforms. If the period is shorter than pulse width + edge time, the edge time and pulse width are adjusted accordingly.
