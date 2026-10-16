# pymeasure.instruments.keithley.Keithley2510.check_temperature_stability

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_temperature_stability(*tolerance=0.1*, *period=10*, *points=64*)

Determine whether the measured temperature remains within tolerance of the temperature setpoint for the requested period.

Parameters:

- **tolerance** – Maximum permitted difference from the temperature setpoint, in degrees Centigrade. (default: `0.1`)

- **period** – Duration, in seconds, used for the stability check. (default: `10`)

Returns:

True if stable, False otherwise.
