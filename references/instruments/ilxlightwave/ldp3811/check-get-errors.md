# pymeasure.instruments.ilxlightwave.LDP3811.check_get_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_get_errors()

After getting a property, check for errors and log them.

Invoked when `check_get_errors=True` is configured for that property.

Override this method if selected errors should raise an Exception.

Returns:

`list` – List of error entries.
