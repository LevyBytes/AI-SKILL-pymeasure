# pymeasure.instruments.keysight.KeysightE3631A.check_set_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_set_errors()

After a property set, inspect errors and log them.

Invoked when that property has `check_set_errors=True`.

Overrides may raise an Exception for selected errors.

Returns:

`list` – List of error entries.
