# pymeasure.instruments.ni.virtualbench.VirtualBench.expand_channel_string

[Owning PyMeasure class, adapter and connection contract](overview.md)

expand_channel_string(*names_in*)

Expands a channel string to a comma-delimited equivalent without colon notation. The final element gives the channel count. `'dig/0:2'` -> `('dig/0, dig/1, dig/2',3)`

Parameters:

**names_in** (*str*) – Channel string

Returns:

Channel string with every channel comma-separated, plus number of channels

Return type:

(str, int)
