# pymeasure.instruments.anritsu.AnritsuMS464xB.max_number_of_points

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *max_number_of_points*: Any*

Set the maximum sweep-point count the instrument can measure.

Changing this value reboots the instrument. Valid values are 25000 and 100000. With 25000 points selected, the instrument supports 16 channels with 16 traces each; with 100000 selected, it supports 1 channel with 16 traces.
