# pymeasure.instruments.srs.ldc500series.LDC500SeriesTEC.current_limit

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *current_limit*: Any*

Set/read TEC current limit in A, as a float strictly in range -4.5 to 4.5.

Reducing `current_limit` below `current_setpoint` makes `current_setpoint` follow `current_limit` downward.
