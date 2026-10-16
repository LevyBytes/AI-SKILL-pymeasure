# pymeasure.instruments.temptronic.ATSBase.temperature

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *temperature*: Any*

Return current temperature at 0.1 ?C resolution.

Type:

float

Temperature reading source is determined by `dut_mode`; values higher than 400 (?C) indicate invalidity.
