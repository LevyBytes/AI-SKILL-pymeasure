# pymeasure.instruments.keithley.Keithley2000

*class *pymeasure.instruments.keithley.Keithley2000(*adapter*, *name='Keithley 2000 Multimeter'*, ***kwargs*)

Bases: `KeithleyBuffer`, `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the Keithley 2000 Multimeter and exposes a higher-level interface for controlling the instrument.

```python
from pymeasure.instruments.keithley.keithley2000 import Keithley2000

meter = Keithley2000("GPIB::1")
meter.measure_voltage()
print(meter.voltage)

```
