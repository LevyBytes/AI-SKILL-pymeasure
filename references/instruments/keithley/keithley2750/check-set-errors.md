# pymeasure.instruments.keithley.Keithley2750.check_set_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_set_errors()

After assigning a property, inspect and log any reported errors.

Runs when that property has `check_set_errors=True` configured.

Subclasses that override this method can raise an Exception for selected error conditions.

Returns:

`list` – List of error entries.
