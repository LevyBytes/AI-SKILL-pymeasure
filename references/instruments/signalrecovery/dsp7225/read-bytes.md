# pymeasure.instruments.signalrecovery.DSP7225.read_bytes

[Owning PyMeasure class, adapter and connection contract](overview.md)

read_bytes(*count*, ***kwargs*)

Read a specified number of bytes from the instrument.

Parameters:

- **count** (*int*) – Number of bytes to read. A value of -1 means read the entire read buffer.

- **kwargs** – Keyword arguments passed to the adapter.

Returns bytes:

Instrument byte response, including termination.

Return type:

`bytes`
