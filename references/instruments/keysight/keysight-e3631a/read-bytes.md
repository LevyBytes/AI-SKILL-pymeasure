# pymeasure.instruments.keysight.KeysightE3631A.read_bytes

[Owning PyMeasure class, adapter and connection contract](overview.md)

read_bytes(*count*, ***kwargs*)

Read a specified byte count from the instrument.

Parameters:

- **count** (*int*) – Number of bytes requested. A value of -1 means read the complete buffer.

- **kwargs** – Keyword arguments forwarded to the adapter.

Returns bytes:

Instrument byte response, including termination.

Return type:

`bytes`
