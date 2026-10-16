# pymeasure.instruments.keysight.KeysightDSOX1102G.waveform_points

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *waveform_points*: Any*

Integer parameter setting how many waveform points waveform_data transfers. Allowed values are 100, 250, 500, and 1000; then 2 000, 5 000, 10 000, 20 000, 50 000, and 62 500.

Note that the oscilloscope may return fewer than the requested nb of points.
