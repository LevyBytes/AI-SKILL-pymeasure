# pymeasure.instruments.common_base.CommonBase.check_set_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_set_errors()

After writing a property, inspect and log instrument errors.

This runs when `check_set_errors=True` is configured on that property.

An overriding implementation may raise an Exception for selected errors.

Returns:

`list` – List of error entries.
