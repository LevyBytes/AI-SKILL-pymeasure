# pymeasure.instruments.lecroy.LeCroyT3DSO1204.check_get_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_get_errors()

After a property get, check for errors and log any that are present.

Used when that property has `check_get_errors=True`.

An override may raise an Exception for selected errors.

Returns:

`list` – List of error entries.
