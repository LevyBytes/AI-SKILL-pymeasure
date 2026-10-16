# pymeasure.instruments.keysight.Keysight81160A.ask

[Owning PyMeasure class, adapter and connection contract](overview.md)

ask(*command*, *query_delay=None*)

Send a command to the instrument, then read and return its response.

Parameters:

- **command** (`str`) – Command string sent to the instrument.

- **query_delay** (`Optional`[`float`]) – Seconds to wait between the write operation and the read operation. (default: `None`)

Returns:

`str` – Device response string with read_termination removed.
