# pymeasure.instruments.thyracont.smartline_v1.SmartlineV1.check_set_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_set_errors()

After setting a property, check for errors and log them.

Invoked when `check_set_errors=True` is configured for that property.

Override this method if selected errors should raise an Exception.

Returns:

List of error entries.
