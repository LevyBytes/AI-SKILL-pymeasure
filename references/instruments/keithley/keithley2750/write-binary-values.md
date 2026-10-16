# pymeasure.instruments.keithley.Keithley2750.write_binary_values

[Owning PyMeasure class, adapter and connection contract](overview.md)

write_binary_values(*command*, *values*, **args*, ***kwargs*)

Transmit binary values to the device.

Parameters:

- **command** (`str`) – Command to send.

- **values** (`Sequence`[`Union`[`int`, `float`]]) — Values that will be transmitted.

- ****kwargs** (**args**,*) — Additional arguments passed through to the Adapter.

Return type:

`None`
