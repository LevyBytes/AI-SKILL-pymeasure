# pymeasure.instruments.keysight.KeysightPNA.byte_order_swapped

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *byte_order_swapped*: Any*

Enable or disable swapped byte order during data transfer (bool).

Some computers receive analyzer data in reverse order. This property only applies when `data_format` is `real32` or `real64`. With `data_format` set to `ascii`, `byte_order_swapped` has no effect.

- `True`: Use with IBM compatible computers.

- `False`: Use when the controller is anything other than an IBM compatible computers

or when VEE, LabView, or T&M Tool kit is being used.
