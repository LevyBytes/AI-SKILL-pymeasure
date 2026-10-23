# pymeasure.instruments.keysight.KeysightE36312A.binary_values

[Owning PyMeasure class, adapter and connection contract](overview.md)

binary_values(*command*, *query_delay=None*, ***kwargs*)

Send a command to the instrument, then return binary data as a numpy array.

Parameters:

- **command** (`str`): Command sent to the instrument.

- **query_delay** (`Optional`[`float`]): Seconds to wait between write and read operations. (default: `None`)

- **kwargs**: Arguments forwarded to `read_binary_values()`.

Returns:

NumPy array of values.
