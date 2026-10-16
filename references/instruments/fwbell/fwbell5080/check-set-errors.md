# pymeasure.instruments.fwbell.FWBell5080.check_set_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_set_errors()

After setting a property, check for errors and log them.

Invoked for a property when `check_set_errors=True` is set.

Override this method if specific errors should raise an Exception.

Returns:

`list` – List of error entries.
