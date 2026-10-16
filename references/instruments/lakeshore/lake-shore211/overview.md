# pymeasure.instruments.lakeshore.LakeShore211

*class *pymeasure.instruments.lakeshore.LakeShore211(*adapter*, *name='Lake Shore 211 Temperature Monitor'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the Lake Shore 211 Temperature Monitor, exposing a high-level interface for instrument interaction.

Docstrings identify any properties and methods that remain untested.

```python
from pymeasure.instruments.lakeshore.lakeshore211 import LakeShore211

controller = LakeShore211("GPIB::1")

print(controller.temperature_celsius)     # Print the sensor temperature in celsius

```
