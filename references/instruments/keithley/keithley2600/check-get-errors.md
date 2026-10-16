# pymeasure.instruments.keithley.Keithley2600.check_get_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_get_errors()

After a property read, inspect the error queue and log any entries.

Used for a property when `check_get_errors=True` has been enabled.

Overrides may raise an Exception for selected errors.

Returns:

`list` – List of error entries.
