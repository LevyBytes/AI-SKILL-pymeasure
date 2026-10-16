# pymeasure.adapters.FakeAdapter.write_binary_values

[Owning PyMeasure class, adapter and connection contract](overview.md)

write_binary_values(*command*, *values*, *termination=''*, ***kwargs*)

Send binary data to the instrument, for example a signal-generator waveform.

Parameters:

- **command** (`str`) - command string sent to the instrument

- **values** (`Sequence`[`Union`[`int`, `float`]]) - iterable representing binary values

- **termination** (`str`) - String appended after the data to terminate the message. (default: `''`)

- ****kwargs** - Key-word arguments forwarded to `Adapter._format_binary_values()`

Returns:

`int` – number of bytes written
