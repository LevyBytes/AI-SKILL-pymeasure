# pymeasure.instruments.srs.ldc500series.LDC500SeriesTEC.check_temperature_stability

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_temperature_stability(*tolerance=0.1*, *period=10*, *points=64*)

Check whether temperature stays stable at the temperature setpoint for a requested interval.

Parameters:

- **tolerance** – Largest permitted offset from temperature setpoint, in degrees Centigrade. (default: `0.1`)

- **period** – Duration used for the stability check, in seconds. (default: `10`)

Returns:

True if stable, False otherwise.
