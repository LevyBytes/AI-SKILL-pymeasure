# pymeasure.instruments.srs.ldc500series.LDC500SeriesTEC.wait_for_temperature_stable

[Owning PyMeasure class, adapter and connection contract](overview.md)

wait_for_temperature_stable(*tolerance=0.1*, *period=10*, *should_stop=<function LDC500SeriesTEC.&lt;lambda&gt;>*, *timeout=60*)

Block execution until the temperature reaches stability at the temperature setpoint.

Parameters:

- **tolerance** – Largest permitted offset from temperature setpoint, in degrees Centigrade. (default: `0.1`)

- **period** – Duration used for the stability check, in seconds. (default: `10`)

- **should_stop** – Function returning True requests that waiting stop. (default: `<function LDC500SeriesTEC.<lambda> at 0x7aa57d9701a0>`)

- **timeout** – Upper bound for waiting time, in seconds. (default: `60`)

Returns:

Returns True once stable, or False when should_stop stops the wait.

Raises:

**TimeoutError** – Raised when temperature has not stabilized before the timeout period ends.
