# pymeasure.instruments.aja.DCXS.ask

[Owning PyMeasure class, adapter and connection contract](overview.md)

ask(*command*, *query_delay=None*, ***kwargs*)

Send a command to the instrument, then read and return its response.

Parameters:

- **command** – Command string to send to the instrument.

- **query_delay** – Seconds to wait between the write and the read. (default: `None`)

- ****kwargs** – Keyword arguments forwarded to the read method.

Returns:

Device response string with read_termination removed.
