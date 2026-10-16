# pymeasure.adapters.SerialAdapter.write_binary_values

[Owning PyMeasure class, adapter and connection contract](overview.md)

write_binary_values(*command*, *values*, *termination=''*, ***kwargs*)

Send binary data to the instrument, such as a waveform for signal generators.

Parameters:

- **command** (`str`) – command string sent to the instrument

- **values** (`Sequence`[`Union`[`int`, `float`]]) – iterable containing the binary values

- **termination** (`str`) – String appended after the payload to end the message. (default: `''`)

- ****kwargs** – Key-word arguments forwarded to `Adapter._format_binary_values()`

Returns:

`int` – number of bytes written
