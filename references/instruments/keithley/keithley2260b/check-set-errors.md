# pymeasure.instruments.keithley.Keithley2260B.check_set_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_set_errors()

After a property write, inspect the error queue and log any entries.

Used for a property when `check_set_errors=True` has been enabled.

Overrides may raise an Exception for selected errors.

Returns:

`list` – List of error entries.
