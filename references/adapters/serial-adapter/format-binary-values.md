# pymeasure.adapters.SerialAdapter._format_binary_values

[Owning PyMeasure class, adapter and connection contract](overview.md)

_format_binary_values(*values*, *datatype='f'*, *is_big_endian=False*, *header_fmt='ieee'*)

Encode values into binary form for internal use by `Adapter.write_binary_values()`.

Parameters:

- **values** (`Sequence`[`Union`[`int`, `float`]]) – data that will be written to the device.

- **datatype** (`Literal`[`'s'`, `'b'`, `'B'`, `'h'`, `'H'`, `'i'`, `'I'`, `'l'`, `'L'`, `'q'`, `'Q'`, `'f'`, `'d'`]) – single-element format string; accepted codes include ‘b’ and ‘B’, ‘h’ and ‘H’, ‘i’ and ‘I’, ‘l’ and ‘L’, ‘q’ and ‘Q’, ‘f’ and ‘d’, plus ‘s’. (default: `'f'`)

- **is_big_endian** (`bool`) – boolean that selects endianness. (default: `False`)

- **header_fmt** (`str`) – header prefix style applied before the data (“ieee”, “hp”, “empty”). (default: `'ieee'`)

Returns:

`bytes` – binary string.
