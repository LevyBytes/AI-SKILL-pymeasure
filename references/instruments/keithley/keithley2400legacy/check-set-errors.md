# pymeasure.instruments.keithley.Keithley2400Legacy.check_set_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_set_errors()

After a property set operation, check for errors and log them.

Called when `check_set_errors=True` is set for that property.

When overriding this method, you can raise an Exception for selected errors.

Returns:

`list` – List of error entries.
