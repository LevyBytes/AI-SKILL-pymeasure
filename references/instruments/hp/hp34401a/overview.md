# pymeasure.instruments.hp.HP34401A

*class *pymeasure.instruments.hp.HP34401A(*adapter*, *name='HP 34401A'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Model wrapper for the HP / Agilent / Keysight 34401A Multimeter, exposing high-level operations for the instrument.

```python
from pymeasure.instruments.hp.hp34401A import HP34401A

dmm = HP34401A("GPIB::1")
dmm.function_ = "DCV"
print(dmm.reading)  # -> Single float reading

dmm.nplc = 0.02
dmm.autozero_enabled = False
dmm.trigger_count = 100
dmm.trigger_delay = "MIN"
print(dmm.reading)  # -> Array of 100 very fast readings

```
