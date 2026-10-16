# pymeasure.instruments.keysight.Keysight81160A.check_set_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_set_errors()

After a property set operation, check for instrument errors and log any findings.

Invoked for a property when `check_set_errors=True` is configured.

Override this method if selected errors should raise an Exception.

Returns:

`list` – List of error entries.
