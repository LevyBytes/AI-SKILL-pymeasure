# pymeasure.instruments.signalrecovery.DSP7225.check_get_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_get_errors()

After getting a property, check for errors and log them.

This is called when `check_get_errors=True` is configured for that property.

An override of this method can raise an Exception for selected errors.

Returns:

`list` – List of error entries.
