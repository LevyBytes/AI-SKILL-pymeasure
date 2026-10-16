# pymeasure.instruments.agilent.Agilent8257D

*class *pymeasure.instruments.agilent.Agilent8257D(*adapter*, *name='Agilent 8257D RF Signal Generator'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Describes the Agilent 8257D Signal Generator and exposes a higher-level interface for working with the instrument.

```python
from pymeasure.instruments.agilent.agilent8257D import Agilent8257D

generator = Agilent8257D("GPIB::1")

generator.power = 0                     # Sets the output power to 0 dBm
generator.frequency = 5                 # Sets the output frequency to 5 GHz
generator.enable()                      # Enables the output

```
