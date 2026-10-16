# pymeasure.instruments.srs.ldc500series.LDC500SeriesLD.current_limit

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *current_limit*: Any*

Set or read the laser diode current limit as a float in mA.

The output current is capped so it cannot rise above `current_limit` in any situation. Lowering `current_limit` beneath `current_setpoint` pulls `current_setpoint` down to match `current_limit`.
