# pymeasure.adapters.PrologixAdapter._format_binary_values

[Owning PyMeasure class, adapter and connection contract](overview.md)

_format_binary_values(*values*, *datatype='f'*, *is_big_endian=False*, *header_fmt='ieee'*)

Encode values as binary data for internal use by `write_binary_values()`.

Parameters:

- **values** – data that will be written to the device.

- **datatype** – single-element format string; see struct module. (default: `'f'`)

- **is_big_endian** – boolean that selects endianess. (default: `False`)

- **header_fmt** – Header prefix style applied before the data (“ieee”, “hp”, “empty”). (default: `'ieee'`)

Returns:

binary string.

Return type:

bytes

## Related property contracts

- Open when checking pymeasure.adapters.PrologixAdapter.auto: [auto](auto.md).
