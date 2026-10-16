# pymeasure.instruments.texio.TexioPSW360L30.check_set_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_set_errors()

After writing a property, check for errors and log anything reported.

Invoked for a property when `check_set_errors=True` is configured.

An override may raise an Exception for chosen error conditions.

Returns:

`list` – List of error entries.
