# pymeasure.instruments.fwbell.FWBell5080.check_get_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_get_errors()

After getting a property, check for errors and log them.

Invoked for a property when `check_get_errors=True` is set.

Override this method if specific errors should raise an Exception.

Returns:

`list` – List of error entries.
