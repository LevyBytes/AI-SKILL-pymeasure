# pymeasure.instruments.anritsu.AnritsuMS464xB.number_of_channels

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *number_of_channels*: Any*

Set how many channels are displayed and therefore accessible.

In 25000 points mode, the channel count may be 1, 2, 3, 4, 6, 8, 9, 10, 12, or 16; in 100000 points mode, only 1 channel is supported. If the provided value is invalid for the current mode, the instrument selects the next higher channel number.
