# pymeasure.instruments.texio.TexioPSW360L30.read_bytes

[Owning PyMeasure class, adapter and connection contract](overview.md)

read_bytes(*count*, ***kwargs*)

Read the requested byte count from the instrument.

Parameters:

- **count** (*int*) — Byte count to read; -1 means the entire read buffer is read.

- **kwargs** — Keyword arguments passed to the adapter.

Returns bytes:

Bytes returned by the instrument, including termination.

Return type:

`bytes`
