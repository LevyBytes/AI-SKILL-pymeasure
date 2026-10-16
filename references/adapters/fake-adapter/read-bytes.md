# pymeasure.adapters.FakeAdapter.read_bytes

[Owning PyMeasure class, adapter and connection contract](overview.md)

read_bytes(*count=-1*, *break_on_termchar=False*, ***kwargs*)

Read a specified byte count from the instrument.

A subclass must not override this.

Parameters:

- **count** (*int*) - Byte count to read. A value of -1 means the whole read buffer is read.

- **break_on_termchar** (*bool*) - Stop reading when a termination character is reached.

- ****kwargs** - Keyword arguments passed to the connection itself.

Returns bytes:

Instrument byte response, including termination.

Return type:

`bytes`
