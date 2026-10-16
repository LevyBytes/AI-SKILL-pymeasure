# pymeasure.instruments.keysight.Keysight81160A.binary_values

[Owning PyMeasure class, adapter and connection contract](overview.md)

binary_values(*command*, *query_delay=None*, ***kwargs*)

Send a command to the instrument and return binary data as a numpy array.

Parameters:

- **command** (`str`) – Command sent to the instrument.

- **query_delay** (`Optional`[`float`]) – Seconds to wait between the write operation and the read operation. (default: `None`)

- **kwargs** – Arguments forwarded to `read_binary_values()`.

Returns:

NumPy array of values.
