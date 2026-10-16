# pymeasure.instruments.andeenhagerling.AH2700A.check_set_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_set_errors()

After a property set operation, check for errors and log any found.

Runs when that property has `check_set_errors=True` configured.

Overriders may raise an Exception for selected errors.

Returns:

`list` – List of error entries.
