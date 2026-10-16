# pymeasure.instruments.keithley.Keithley2200.check_set_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_set_errors()

After a property set, inspect errors and write them to the log.

Runs for properties configured with `check_set_errors=True`.

Overriding this method lets selected errors raise an Exception.

Returns:

`list` – List of error entries.
