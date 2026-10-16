# pymeasure.instruments.Instrument.check_get_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_get_errors()

After reading a property, inspect and log instrument errors.

This runs when `check_get_errors=True` is configured on that property.

An overriding implementation may raise an Exception for selected errors.

Returns:

`list` – List of error entries.
