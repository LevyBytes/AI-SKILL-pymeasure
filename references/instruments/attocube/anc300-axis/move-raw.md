# pymeasure.instruments.attocube.anc300.Axis.move_raw

[Owning PyMeasure class, adapter and connection contract](overview.md)

move_raw(*steps*)

Move `steps` steps according to the argument sign. This non-blocking method assumes the axis mode is already `stp` and returns immediately after sending the command.

Parameters:

**steps** - integer number of steps to perform. Positive values mean upward steps; negative values mean downward steps. +/-inf starts continuous movement, and stop can halt the axis.
