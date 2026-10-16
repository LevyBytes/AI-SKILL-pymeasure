# pymeasure.instruments.attocube.anc300.Axis.move

[Owning PyMeasure class, adapter and connection contract](overview.md)

move(*steps*, *gnd=True*)

Move `steps` steps in the direction indicated by the argument sign. The method automatically changes axis mode and, when `gnd` is True, grounds the axis at the end. It blocks until motion is complete.

Parameters:

- **steps** - finite integer number of steps to perform. Positive values mean upward steps; negative values mean downward steps.

- **gnd** - bool flag selecting whether the axis is grounded after movement completes (default: `True`)
