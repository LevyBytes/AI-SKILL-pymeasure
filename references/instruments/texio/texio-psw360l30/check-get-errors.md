# pymeasure.instruments.texio.TexioPSW360L30.check_get_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_get_errors()

After reading a property, check for errors and log anything reported.

Invoked for a property when `check_get_errors=True` is configured.

Overrides may raise an Exception for selected error conditions.

Returns:

`list` – List of error entries.
