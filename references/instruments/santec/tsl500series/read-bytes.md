# pymeasure.instruments.santec.tsl500series.TSL500Series.read_bytes

[Owning PyMeasure class, adapter and connection contract](overview.md)

read_bytes(*count*, ***kwargs*)

Read the requested byte count from the instrument.

Parameters:

- **count** (*int*) – Number of bytes requested. Use -1 to consume the whole read buffer.

- **kwargs** – Adapter keyword arguments.

Returns bytes:

Instrument response bytes, including termination.

Return type:

`bytes`
