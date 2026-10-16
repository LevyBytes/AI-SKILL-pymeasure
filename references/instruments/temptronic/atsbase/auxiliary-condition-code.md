# pymeasure.instruments.temptronic.ATSBase.auxiliary_condition_code

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *auxiliary_condition_code*: Any*

Get out auxiliary condition status register.

Type:

int

Relevant flags are:

| Bit | Meaning |
| --- | --- |
| 10 | None |
| 9 | Ramp mode |
| 8 | Mode: 0 programming, 1 manual |
| 7 | None |
| 6 | TS status: 0 start-up, 1 ready |
| 5 | Flow: 0 off, 1 on |
| 4 | Sense mode: 0 air, 1 DUT |
| 3 | Compressor: 0 on, 1 off (heating possible) |
| 2 | Head: 0 lower, upper |
| 1 | None |
| 0 | None |

Consult chapter 4 in the manual
