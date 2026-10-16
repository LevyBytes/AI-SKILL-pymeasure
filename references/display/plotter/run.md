# pymeasure.display.plotter.Plotter.run

[Owning PyMeasure class, adapter and connection contract](overview.md)

run()

Method that defines what the thread does while it is active.

Subclasses may replace this method. The default run() implementation calls the target callable supplied to the object constructor, when one was provided, and passes positional values from args plus keyword values from kwargs.
