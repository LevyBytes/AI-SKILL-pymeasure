# pymeasure.instruments.keithley.Keithley2400Legacy.check_get_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_get_errors()

After a property get operation, check for errors and log them.

Called when `check_get_errors=True` is set for that property.

When overriding this method, you can raise an Exception for selected errors.

Returns:

`list` – List of error entries.
