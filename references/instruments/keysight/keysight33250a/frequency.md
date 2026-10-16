# pymeasure.instruments.keysight.Keysight33250A.frequency

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *frequency*: Any*

Get or set output waveform frequency in Hz (float, strict from 1e-6 to 80e6). The valid range depends on function: SIN/SQU 1e-6 to 80e6, RAMP 1e-6 to 1e6, PULS 500e-6 to 50e6, USER/ARB 1e-6 to 25e6.
