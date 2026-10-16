# pymeasure.instruments.Channel.write

[Owning PyMeasure class, adapter and connection contract](overview.md)

write(*command*, ***kwargs*)

Send a string command to the instrument with write_termination appended.

Parameters:

- **command** (`str`) – command string sent to the instrument. The channel id replaces ‘{ch}’.

- **kwargs** – Keyword arguments passed to the adapter.

Return type:

`None`
