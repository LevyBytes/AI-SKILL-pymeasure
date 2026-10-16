# pymeasure.adapters.PrologixAdapter.write

[Owning PyMeasure class, adapter and connection contract](overview.md)

write(*command*, ***kwargs*)

Send a string command to the instrument with write_termination appended.

If `address` has a GPIB address, that address is sent before the command.

Parameters:

- **command** (*str*) – Command string sent to the instrument, excluding termination.

- **kwargs** – Keyword arguments forwarded to the underlying connection.
