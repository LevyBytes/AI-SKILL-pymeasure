# pymeasure.instruments.keithley.Keithley2260B.read_bytes

[Owning PyMeasure class, adapter and connection contract](overview.md)

read_bytes(*count*, ***kwargs*)

Read the requested byte count from the instrument.

Parameters:

- **count** (*int*) – Bytes requested from the instrument. Use -1 to consume the full read buffer.

- **kwargs** – Adapter keyword arguments.

Returns bytes:

Instrument byte response, including termination.

Return type:

`bytes`
