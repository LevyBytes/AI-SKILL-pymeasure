# pymeasure.instruments.andeenhagerling.AH2700A.check_get_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_get_errors()

After a property get operation, check for errors and log any found.

Runs when that property has `check_get_errors=True` configured.

Overriders may raise an Exception for selected errors.

Returns:

`list` – List of error entries.
