# pymeasure.instruments.ni.virtualbench.VirtualBench.collapse_channel_string

[Owning PyMeasure class, adapter and connection contract](overview.md)

collapse_channel_string(*names_in*)

Compacts a channel string into an equivalent comma- and colon-delimited form. The final element gives the channel count.

Parameters:

**names_in** (*str*) – Channel string

Returns:

Channel string using colon notation where available, plus number of channels

Return type:

(str, int)
