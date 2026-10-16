# pymeasure.instruments.teledyne.TeledyneT3AFG.check_get_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_get_errors()

After a property get, check for errors and log any found.

This is invoked when `check_get_errors=True` has been configured for that property.

An override of this method may raise an Exception for selected errors.

Returns:

`list` – List of error entries.
