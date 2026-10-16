# pymeasure.instruments.deltaelektronika.SM7045D

*class *pymeasure.instruments.deltaelektronika.SM7045D(*adapter*, *name='Delta Elektronika SM 70-45 D'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Class for the SM 70-45 D power supply.

```python
from pymeasure.instruments.deltaelektronika.sm7045d import SM7045D

source = SM7045D("GPIB::8")

source.ramp_to_zero(1)               # Set output to 0 before enabling
source.enable()                      # Enables the output
source.current = 1                   # Sets a current of 1 Amps

```
