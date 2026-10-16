# pymeasure.instruments.aimtti.aimttiPL.PLBase

*class *pymeasure.instruments.aimtti.aimttiPL.PLBase(*adapter*, *name='AimTTI PL'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Control AimTTI PL series power supplies. Models whose number ends in -P or P(G) implement this remote interface.

Documentation:

[https://resources.aimtti.com/manuals/New_PL+PL-P_Series_Instruction_Manual-Iss18.pdf](https://resources.aimtti.com/manuals/New_PL+PL-P_Series_Instruction_Manual-Iss18.pdf)

PL-series devices:

[https://www.aimtti.com/product-category/dc-power-supplies/aim-plseries](https://www.aimtti.com/product-category/dc-power-supplies/aim-plseries)

The timeout argument defaults to 5000ms.

```python
from pymeasure.instruments.aimtti.aimttiPL import PL303QMDP

psu = PL303QMDP("ASRL7::INSTR")
psu.reset()
psu.ch_2.voltage = 1.2
psu.ch_2.output_enabled = True
...
psu.ch_2.output_enabled = False
psu.local()

```
