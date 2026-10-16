# pymeasure.instruments.lakeshore.LakeShore224

*class *pymeasure.instruments.lakeshore.LakeShore224(*adapter*, *name='Lakeshore Model 224 Temperature Controller'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the Lakeshore 224 Temperature monitor with a high-level interface to the instrument. The 224 includes 12 temperature input channels (A, B, C1-5, D1-5). This driver uses the [LakeShore Channel Classes](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#lakeshorechannels)

```python
from pymeasure.instruments.lakeshore.lakeshore224 import LakeShore224

monitor = LakeShore224('GPIB::1')

print(monitor.input_A.kelvin)           # Print the temperature in kelvin on sensor A
monitor.input_A.wait_for_temperature()  # Wait for the temperature on sensor A to stabilize.

```
