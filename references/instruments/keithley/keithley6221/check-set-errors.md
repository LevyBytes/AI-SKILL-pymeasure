# pymeasure.instruments.keithley.Keithley6221.check_set_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_set_errors()

After assigning a property value, inspect instrument errors and log any findings.

Runs when `check_set_errors=True` has been configured for that property.

Overrides may raise an Exception for selected error conditions.

Returns:

`list` – List of error entries.
