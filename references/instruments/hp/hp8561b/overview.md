# pymeasure.instruments.hp.HP8561B

*class *pymeasure.instruments.hp.HP8561B(*adapter*, *name='Hewlett-Packard HP8561B'*, ***kwargs*)

Bases: `HP856Xx`

Represents the HP 8561B Spectrum Analyzer, exposing a high-level interface for operating the instrument.

```python
from pymeasure.instruments.hp import HP8561B
from pymeasure.instruments.hp.hp856Xx import AmplitudeUnits

sa = HP8561B("GPIB::1")

sa.amplitude_unit = AmplitudeUnits.DBUV
sa.start_frequency = 6.4e9
sa.stop_frequency = 6.5e9

print(sa.marker_amplitude)

```
