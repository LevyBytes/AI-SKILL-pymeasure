# pymeasure.instruments.keithley.Keithley2400.check_get_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_get_errors()

After reading a property, check for errors and log any that are found.

Invoked when that property has `check_get_errors=True`.

Override this method if selected errors should be raised as an Exception.

Returns:

`list` – List of error entries.
