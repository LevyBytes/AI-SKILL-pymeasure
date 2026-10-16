# pymeasure.instruments.srs.SR830.err_status

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *err_status*: Any*

Read the lockin error (ERR) status byte. The result is an IntFlag whose string positions map to error flags:

| Bit | Status |
| --- | --- |
| 0 | unused |
| 1 | backup error |
| 2 | RAM error |
| 3 | unused |
| 4 | ROM error |
| 5 | GPIB error |
| 6 | DSP error |
| 7 | DSP error |
