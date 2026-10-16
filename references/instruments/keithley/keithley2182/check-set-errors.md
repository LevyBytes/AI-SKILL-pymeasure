# pymeasure.instruments.keithley.Keithley2182.check_set_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_set_errors()

After a property write, inspect the error queue and log any entries.

Invoked when that property has `check_set_errors=True` configured.

Overrides may raise an Exception for selected errors.

Returns:

`list` – List of error entries.
