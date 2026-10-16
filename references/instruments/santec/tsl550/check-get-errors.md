# pymeasure.instruments.santec.tsl550.TSL550.check_get_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_get_errors()

After a property read, inspect for errors and write them to the log.

Invoked for a property when `check_get_errors=True` is enabled.

Overriding this method can include raising an Exception for selected errors.

Returns:

`list` – List of error entries.
