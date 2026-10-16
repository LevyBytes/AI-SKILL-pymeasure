# Graphical displays

PyMeasure can generate graphical user interfaces (GUIs) to control measurement procedure execution. Those interfaces support live plotting for data and include a queue system for coordinating large numbers of experiments.

The [Using a graphical interface](https://pymeasure.readthedocs.io/en/latest/tutorial/graphical.html) tutorial walks through these capabilities.

 (Figure: ManagedWindow Running Example)

The GUIs can work with more than the instruments bundled in this package. Any python instrument may be used. As an example, [this script](https://github.com/pymeasure/pymeasure/tree/master/examples/Basic/gui_foreign_instrument.py) shows use of an [InstrumentKit](https://instrumentkit.readthedocs.io) instrument.
