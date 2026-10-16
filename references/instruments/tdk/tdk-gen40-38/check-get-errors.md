# pymeasure.instruments.tdk.tdk_gen40_38.TDK_Gen40_38.check_get_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_get_errors()

After a property get, inspect for errors and log any findings.

Invoked for a property when `check_get_errors=True` is configured.

Overriding this method lets you raise an Exception for selected errors.

Returns:

`list` – List of error entries.
