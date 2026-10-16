# pymeasure.instruments.santec.tsl500series.TSL500Series.check_set_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_set_errors()

After a property write, inspect for errors and write them to the log.

Invoked for a property when `check_set_errors=True` is enabled.

Overriding this method can include raising an Exception for selected errors.

Returns:

`list` – List of error entries.
