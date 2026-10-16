# pymeasure.instruments.lakeshore.LakeShore421

Covers: Lake Shore 421 Gaussmeter; Lake Shore 331 Temperature Controller.

## Lake Shore 421 Gaussmeter

### Lake Shore 421 Gaussmeter

 *class *pymeasure.instruments.lakeshore.LakeShore421(*adapter*, *name='Lake Shore 421 Gaussmeter'*, *baud_rate=9600*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the Lake Shore 421 Gaussmeter and exposes a high-level interface for working with the instrument.

```python
from pymeasure.instruments.lakeshore.lakeshore421 import LakeShore421

gaussmeter = LakeShore421("COM1")
gaussmeter.unit = "T"               # Set units to Tesla
gaussmeter.auto_range = True        # Turn on auto-range
gaussmeter.fast_mode = True         # Turn on fast-mode

```

The driver inserts 50 ms between writes because the instrument cannot reliably process faster write timing.
