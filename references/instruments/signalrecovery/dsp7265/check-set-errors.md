# pymeasure.instruments.signalrecovery.DSP7265.check_set_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_set_errors()

After writing a property, check for errors and log what is found.

Used when that property has `check_set_errors=True`.

Override this method if some errors should raise an Exception.

Returns:

`list` – List of error entries.
