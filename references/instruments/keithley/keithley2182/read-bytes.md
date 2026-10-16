# pymeasure.instruments.keithley.Keithley2182.read_bytes

[Owning PyMeasure class, adapter and connection contract](overview.md)

read_bytes(*count*, ***kwargs*)

Read the requested byte count from the instrument.

Parameters:

- **count** (*int*) – Byte count to read. A value of -1 reads the complete read buffer.

- **kwargs** – Keyword arguments passed to the adapter.

Returns bytes:

Bytes returned by the instrument, including termination.

Return type:

`bytes`
