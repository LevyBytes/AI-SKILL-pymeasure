# pymeasure.instruments.keithley.Keithley2600.write_binary_values

[Owning PyMeasure class, adapter and connection contract](overview.md)

write_binary_values(*command*, *values*, **args*, ***kwargs*)

Send binary values to the device.

Parameters:

- **command** (`str`) – Command to send.

- **values** (`Sequence`[`Union`[`int`, `float`]]) – Values that will be transmitted.

- ****kwargs** (**args**,*) – Additional arguments forwarded to the Adapter.

Return type:

`None`
