# pymeasure.adapters.PrologixAdapter.write_binary_values

[Owning PyMeasure class, adapter and connection contract](overview.md)

write_binary_values(*command*, *values*, ***kwargs*)

Send binary data to the instrument, such as a waveform for signal generators.

values are encoded as an IEEE 488.2 Definite Length Arbitrary Block Response Data block.

Parameters:

- **command** – SCPI command sent to the instrument

- **values** – iterable containing the binary values

- **kwargs** – Key-word arguments forwarded to `_format_binary_values()`

Returns:

number of bytes written
