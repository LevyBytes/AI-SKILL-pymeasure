# pymeasure.adapters.PrologixAdapter.gpib

[Owning PyMeasure class, adapter and connection contract](overview.md)

gpib(*address*, ***kwargs*)

Return a PrologixAdapter object for the requested GPIB address while reusing the Serial connection shared by other invocations of this function.

Parameters:

- **address** – Integer GPIB address for the target instrument

- **kwargs** – Arguments for the initialization

Returns:

PrologixAdapter for specific GPIB address

## Related property contracts

- Open when checking pymeasure.adapters.PrologixAdapter.gpib_read_timeout: [gpib_read_timeout](gpib-read-timeout.md).
