# pymeasure.adapters.Adapter.write

[Owning PyMeasure class, adapter and connection contract](overview.md)

write(*command*, ***kwargs*)

Send a string command to the instrument with write_termination appended.

Subclass implementations must not replace this method.

Parameters:

- **command** (*str*) – Command string sent to the instrument, excluding termination.

- ****kwargs** – Keyword arguments forwarded to the underlying connection.

Return type:

`None`
