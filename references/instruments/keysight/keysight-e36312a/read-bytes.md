# pymeasure.instruments.keysight.KeysightE36312A.read_bytes

[Owning PyMeasure class, adapter and connection contract](overview.md)

read_bytes(*count*, ***kwargs*)

Read a specified byte count from the instrument.

Parameters:

- **count** (*int*) — Number of bytes requested. A value of -1 means the entire read buffer is read.

- **kwargs** — Keyword arguments passed to the adapter.

Returns bytes:

Instrument byte response, including termination.

Return type:

`bytes`
