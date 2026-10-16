# pymeasure.instruments.lecroy.LeCroyT3DSO1204.ask

[Owning PyMeasure class, adapter and connection contract](overview.md)

ask(*command*, *query_delay=None*)

Send a command to the instrument and return the response that is read back.

Parameters:

- **command** (`str`) – Command string sent to the instrument.

- **query_delay** (`Optional`[`float`]) – Seconds to wait between the write and read operations. (default: `None`)

Returns:

`str` – Device response string with read_termination removed.
