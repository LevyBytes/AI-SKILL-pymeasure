# pymeasure.instruments.velleman.VellemanK8090.check_set_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_set_errors()

After setting a property, check for errors and log any found.

Used when `check_set_errors=True` is configured on that property.

After a switch command, the K8090 returns status only when at least one switch actually changed. This code tries to drain the buffer so it is empty. It does not perform real error checking here.

Returns:

List of error entries.
