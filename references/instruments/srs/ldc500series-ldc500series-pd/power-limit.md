# pymeasure.instruments.srs.ldc500series.LDC500SeriesPD.power_limit

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *power_limit*: Any*

Set/read the photodiode power limit in mW when `mode == "CP"` and `photodiode_units == "mW"`; value type is float.

When `power_limit` is lowered beneath `power_setpoint`, `power_setpoint` is pulled down with `power_limit`.
