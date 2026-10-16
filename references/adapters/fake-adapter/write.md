# pymeasure.adapters.FakeAdapter.write

[Owning PyMeasure class, adapter and connection contract](overview.md)

write(*command*, ***kwargs*)

Send a string command to the instrument after appending write_termination.

A subclass must not override this.

Parameters:

- **command** (*str*) - Command string sent to the instrument, without termination.

- ****kwargs** - Keyword arguments passed to the connection itself.

Return type:

`None`
