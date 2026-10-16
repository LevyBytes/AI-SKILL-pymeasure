# pymeasure.instruments.keithley.Keithley2450.check_get_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_get_errors()

After a property get, inspect errors and log any found.

Invoked when that property has `check_get_errors=True`.

Overrides of this method may raise an Exception for selected errors.

Returns:

`list` – List of error entries.
