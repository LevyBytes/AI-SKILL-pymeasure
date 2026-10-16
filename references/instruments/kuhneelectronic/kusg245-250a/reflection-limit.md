# pymeasure.instruments.kuhneelectronic.Kusg245_250A.reflection_limit

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *reflection_limit

Set the reflection limit in Watts; accepted integer choices are 0 for no limit, 100, 150, 180, 200, and 230.

Note

When reflected power hits the configured limit, forward power is lowered to that value and power control stays locked until the user clears the alarm with `clear_VSWR_error()`.
