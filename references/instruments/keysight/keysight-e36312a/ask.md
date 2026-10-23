# pymeasure.instruments.keysight.KeysightE36312A.ask

[Owning PyMeasure class, adapter and connection contract](overview.md)

ask(*command*, *query_delay=None*)

Send a command to the instrument, then return the response that is read back.

Parameters:

- **command** (`str`): Command string sent to the instrument.

- **query_delay** (`Optional`[`float`]): Seconds to wait between write and read operations. (default: `None`)

Returns:

`str`: Device response string with read_termination removed.
