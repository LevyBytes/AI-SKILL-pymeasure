# pymeasure.instruments.advantest.advantestR624X.SMUChannel.null_operation_enabled

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *null_operation_enabled*: Any*

Enable or disable the null operation (bool) (`NUG`).

Type:

bool

Note

- Disabling the null operation does not rewrite null data.

- Null data is rewritten only when the null operation changes from OFF to ON, or when initialization occurs during DC operation or pulse operation.
