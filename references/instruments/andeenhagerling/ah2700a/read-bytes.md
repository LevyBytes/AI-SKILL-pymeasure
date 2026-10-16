# pymeasure.instruments.andeenhagerling.AH2700A.read_bytes

[Owning PyMeasure class, adapter and connection contract](overview.md)

read_bytes(*count*, ***kwargs*)

Read a specified byte count from the instrument.

Parameters:

- **count** (*int*) - Number of bytes to read; -1 means read the entire read buffer.

- **kwargs** - Keyword arguments passed to the adapter.

Returns bytes:

Instrument byte response, including termination.

Return type:

`bytes`
