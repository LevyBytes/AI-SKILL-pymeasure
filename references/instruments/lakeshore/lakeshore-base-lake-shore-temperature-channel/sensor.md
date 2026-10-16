# pymeasure.instruments.lakeshore.lakeshore_base.LakeShoreTemperatureChannel.sensor

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *sensor*: Any*

Read a channel temperature in sensor units.

 Method call: wait_for_temperature with *target*, *unit='kelvin'*, *accuracy=0.1*, *interval=1*, *timeout=360*, and *should_stop=<function LakeShoreTemperatureChannel.&lt;lambda&gt;>*.

Blocks execution until the temperature reaches the target within accuracy (%), checking at each interval in seconds.

Parameters:

- **target** - Target temperature expressed in kelvin, celsius, or sensor units.

- **unit** - Unit used when querying temperature values: 'kelvin', 'celsius', or 'sensor'. (default: `'kelvin'`)

- **accuracy** - Acceptable percentage deviation between target and temperature. (default: `0.1`)

- **interval** - Time interval in seconds between queries. (default: `1`)

- **timeout** - Seconds to wait before raising an exception (default: `360`)

- **should_stop** - Function consulted to stop waiting when it returns True; by default it always returns False (default: `<function LakeShoreTemperatureChannel.<lambda> at 0x7aa5808f6f00>`)
