# pymeasure.instruments.tdk.tdk_gen80_65.TDK_Gen80_65.read_bytes

[Owning PyMeasure class, adapter and connection contract](overview.md)

read_bytes(*count*, ***kwargs*)

Read a requested byte count from the instrument.

Parameters:

- **count** (*int*) – Bytes to read. A value of -1 means read the entire read buffer.

- **kwargs** – Keyword arguments passed to the adapter.

Returns bytes:

Instrument byte response, including termination.

Return type:

`bytes`
