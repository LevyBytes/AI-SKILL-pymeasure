# pymeasure.instruments.keysight.Keysight81160A.check_get_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_get_errors()

After a property get operation, check for instrument errors and log any findings.

Invoked for a property when `check_get_errors=True` is configured.

Override this method if selected errors should raise an Exception.

Returns:

`list` – List of error entries.
