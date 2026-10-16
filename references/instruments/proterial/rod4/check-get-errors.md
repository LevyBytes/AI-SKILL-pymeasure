# pymeasure.instruments.proterial.ROD4.check_get_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_get_errors()

After reading a property, check for errors and log any findings.

This is called when `check_get_errors=True` is configured on that property.

Override this method if some errors should raise an Exception.

Returns:

`list` – List of error entries.
