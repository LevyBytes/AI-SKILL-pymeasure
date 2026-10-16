# pymeasure.instruments.Channel.write_binary_values

[Owning PyMeasure class, adapter and connection contract](overview.md)

write_binary_values(*command*, *values*, **args*, ***kwargs*)

Send binary values to the instrument.

Parameters:

- **command** (`str`) – Command to send.

- **values** (`Sequence`[`Union`[`int`, `float`]]) – Values that will be transmitted.

- ****kwargs** (**args**,*) – Additional arguments passed on to the Adapter.

Return type:

`None`
