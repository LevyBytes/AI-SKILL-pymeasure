# pymeasure.instruments.ptw.ptwUNIDOS.interval_measurement

[Owning PyMeasure class, adapter and connection contract](overview.md)

interval_measurement(*interval=None*)

Execute an interval measurement.

Parameters:

**interval** (`Optional`[`int`]) - optional measurement interval in seconds (default: `None`)

Return type:

`None`

When *interval* is omitted, measurement runs using the current `integration_time` setting.

Note

Write permission is required.
