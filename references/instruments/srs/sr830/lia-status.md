# pymeasure.instruments.srs.SR830.lia_status

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *lia_status*: Any*

Read the lockin amplifier (LIA) status byte. The return is a binary string whose positions map to status flags:

| Bit | Status |
| --- | --- |
| 0 | Input/Amplifier overload |
| 1 | Time constant filter overload |
| 2 | Output overload |
| 3 | Reference unlock |
| 4 | Detection frequency range switched |
| 5 | Time constant changed indirectly |
| 6 | Data storage triggered |
| 7 | unused |
