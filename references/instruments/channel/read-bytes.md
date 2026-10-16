# pymeasure.instruments.Channel.read_bytes

[Owning PyMeasure class, adapter and connection contract](overview.md)

read_bytes(*count*, ***kwargs*)

Read a specified byte count from the instrument.

Parameters:

- **count** (*int*) - Number of bytes to read. A value of -1 requests the entire read buffer.

- **kwargs** - Keyword arguments passed to the adapter.

Returns bytes:
Byte response from the instrument, with termination included.

Return type:

`bytes`
