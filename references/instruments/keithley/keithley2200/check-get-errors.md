# pymeasure.instruments.keithley.Keithley2200.check_get_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_get_errors()

After a property get, inspect errors and write them to the log.

Runs for properties configured with `check_get_errors=True`.

Overriding this method lets selected errors raise an Exception.

Returns:

`list` – List of error entries.
