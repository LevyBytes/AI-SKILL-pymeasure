# pymeasure.instruments.keysight.KeysightE36312A.check_set_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_set_errors()

After a property set, check for errors and log any results.

Invoked when `check_set_errors=True` is configured for that property.

An override of this method may raise an Exception for selected errors.

Returns:

`list` – List of error entries.
