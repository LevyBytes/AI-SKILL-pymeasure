# pymeasure.instruments.keithley.Keithley2510.wait_for_temperature_stable

[Owning PyMeasure class, adapter and connection contract](overview.md)

wait_for_temperature_stable(*tolerance=0.1*, *period=10*, *should_stop=<function Keithley2510.&lt;lambda&gt;>*, *timeout=60*)

Block execution until the temperature reaches stable operation at the temperature setpoint.

Parameters:

- **tolerance** – Allowed maximum difference from the temperature setpoint, in degrees Centigrade. (default: `0.1`)

- **period** – Duration, in seconds, over which stability is evaluated. (default: `10`)

- **should_stop** – Function returning True when waiting should stop. (default: `<function Keithley2510.<lambda> at 0x7aa5835c0880>`)

- **timeout** – Maximum wait duration, in seconds. (default: `60`)

Returns:

True indicates stable operation; False means should_stop stopped the wait.

Raises:

**TimeoutError** – Raised when the temperature remains unstable for the full timeout period.
