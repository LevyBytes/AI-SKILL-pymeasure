# pymeasure.instruments.proterial.ROD4.read_bytes

[Owning PyMeasure class, adapter and connection contract](overview.md)

read_bytes(*count*, ***kwargs*)

Read a specified byte count from the instrument.

Parameters:

- **count** (*int*) - Number of bytes to read. Use -1 to consume the complete read buffer.

- **kwargs** - Keyword arguments passed to the adapter.

Returns bytes:

Instrument byte response, including termination.

Return type:

`bytes`
