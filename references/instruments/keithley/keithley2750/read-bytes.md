# pymeasure.instruments.keithley.Keithley2750.read_bytes

[Owning PyMeasure class, adapter and connection contract](overview.md)

read_bytes(*count*, ***kwargs*)

Read a specified byte count from the instrument.

Parameters:

- **count** (*int*) — Bytes to read. Use -1 to consume the entire read buffer.

- **kwargs** — Adapter-specific keyword arguments.

Returns bytes:

Instrument byte response, including the termination bytes.

Return type:

`bytes`
