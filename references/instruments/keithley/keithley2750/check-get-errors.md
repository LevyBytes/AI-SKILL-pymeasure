# pymeasure.instruments.keithley.Keithley2750.check_get_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_get_errors()

After a property read, inspect and log any reported errors.

Runs when that property has `check_get_errors=True` configured.

Subclasses that override this method can raise an Exception for selected error conditions.

Returns:

`list` – List of error entries.
