# pymeasure.instruments.teledyne.TeledyneOscilloscope.ch

[Owning PyMeasure class, adapter and connection contract](overview.md)

ch(*source*)

Return a channel object by numeric index or channel name. When source is “math”, return the scope object itself instead.

Parameters:

**source** – accepts 1, 2, 3, 4 or C1, C2, C3, C4, MATH

Returns:

handle to the selected source.
