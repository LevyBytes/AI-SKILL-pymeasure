# pymeasure.instruments.keithley.Keithley2000.read_bytes

[Owning PyMeasure class, adapter and connection contract](overview.md)

read_bytes(*count*, ***kwargs*)

Read a specified byte count from the instrument.

Parameters:

- **count** (*int*) — Number of bytes to read. Use -1 to read the complete read buffer.

- **kwargs** — Adapter keyword arguments.

Returns bytes:

Bytes returned by the instrument, including termination.

Return type:

`bytes`
