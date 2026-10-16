# pymeasure.instruments.keithley.Keithley2400Legacy.read_bytes

[Owning PyMeasure class, adapter and connection contract](overview.md)

read_bytes(*count*, ***kwargs*)

Read the requested byte count from the instrument.

Parameters:

- **count** (*int*) - number of bytes to read. -1 means read the whole read buffer.

- **kwargs** - keyword arguments for the adapter.

Returns bytes:

Instrument bytes response, including termination.

Return type:

`bytes`
