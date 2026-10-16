# pymeasure.instruments.keithley.Keithley2700

*class *pymeasure.instruments.keithley.Keithley2700(*adapter*, *name='Keithley 2700 MultiMeter/Switch System'*, ***kwargs*)

Bases: `KeithleyBuffer`, [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Model interface for the Keithley 2700 Multimeter/Switch System, exposing high-level operations for communicating with the instrument.

```python
from pymeasure.instruments.keithley.keithley2700 import Keithley2700

keithley = Keithley2700("GPIB::1")

```
