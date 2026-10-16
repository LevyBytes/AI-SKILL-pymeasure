# pymeasure.instruments.keysight.KeysightE36312A.check_get_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_get_errors()

After a property get, check for errors and log any results.

Invoked when `check_get_errors=True` is configured for that property.

An override of this method may raise an Exception for selected errors.

Returns:

`list` – List of error entries.
