# Instrument ready

PyMeasure ships with several [instrument definitions](https://pymeasure.readthedocs.io/en/latest/api/instruments/index.html) already available. They are grouped by the instrument manufacturer name. For example, the class for the [Keithley 2400 SourceMeter](https://pymeasure.readthedocs.io/en/latest/api/instruments/keithley/keithley2400.html) is imported with:

```python
from pymeasure.instruments.keithley import Keithley2400

```

The [Tutorials](https://pymeasure.readthedocs.io/en/latest/tutorial/index.html) section provides more detail about [connecting to an instrument](https://pymeasure.readthedocs.io/en/latest/tutorial/connecting.html). When the needed instrument is not available and you want to contribute, consult the documentation for [adding an instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).
