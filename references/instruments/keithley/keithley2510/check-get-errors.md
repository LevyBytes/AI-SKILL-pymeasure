# pymeasure.instruments.keithley.Keithley2510.check_get_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_get_errors()

After a property is read, inspect instrument errors and log any findings.

Runs when `check_get_errors=True` has been configured for that property.

Overrides may raise an Exception for selected error conditions.

Returns:

`list` – List of error entries.
