# pymeasure.instruments.keithley.Keithley2450.read_bytes

[Owning PyMeasure class, adapter and connection contract](overview.md)

read_bytes(*count*, ***kwargs*)

Read a specified byte count from the instrument.

Parameters:

- **count** (*int*) - Bytes to read. A value of -1 means read the entire read buffer.

- **kwargs** - Keyword arguments passed to the adapter.

Returns bytes:

Instrument bytes response, including termination.

Return type:

`bytes`
