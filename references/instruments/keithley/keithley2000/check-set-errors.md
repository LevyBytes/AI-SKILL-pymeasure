# pymeasure.instruments.keithley.Keithley2000.check_set_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_set_errors()

After a property write, inspect for errors and log any that are present.

Runs when that property has `check_set_errors=True` configured.

Overrides may raise an Exception for selected error conditions.

Returns:

`list` – List of error entries.
