# pymeasure.instruments.srs.ldc500series.LDC500SeriesLD.modulation_bandwidth

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *modulation_bandwidth*: Any*

Set or read laser diode modulation bandwidth as str “HIGH” or “LOW”.

For the DC coupled analog modulation input, the –3 dB roll-off frequency depends on `mode` and `modulation_bandwidth`:

|  | CC | CP |
| --- | --- | --- |
| LOW | 10kHz | 100Hz |
| HIGH | 1.2mhz | 5kHz |
