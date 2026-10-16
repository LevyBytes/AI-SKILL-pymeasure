# pymeasure.instruments.anaheimautomation.DPSeriesMotorController.absolute_to_steps

[Owning PyMeasure class, adapter and connection contract](overview.md)

absolute_to_steps(*pos*)

Convert an absolute position into a step count for the move. Subclasses must implement this.

Parameters:

**pos** - Absolute position, using the units selected by the subclassed `absolute_to_steps()` method.
