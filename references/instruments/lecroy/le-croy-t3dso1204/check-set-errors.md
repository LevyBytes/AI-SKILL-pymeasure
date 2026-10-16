# pymeasure.instruments.lecroy.LeCroyT3DSO1204.check_set_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_set_errors()

After a property set, check for errors and log any that are present.

Used when that property has `check_set_errors=True`.

An override may raise an Exception for selected errors.

Returns:

`list` – List of error entries.
