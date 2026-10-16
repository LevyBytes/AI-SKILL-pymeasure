# pymeasure.adapters.PrologixAdapter.reset

[Owning PyMeasure class, adapter and connection contract](overview.md)

reset()

Issue a power-on reset to the controller.

This operation lasts about 5 seconds; input received during that interval is ignored, and the connection is closed.

## Related property contracts

- Open when checking pymeasure.adapters.PrologixAdapter.version: [version](version.md).
