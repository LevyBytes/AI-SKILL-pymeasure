# pymeasure.instruments.hp.HP8560A

*class *pymeasure.instruments.hp.HP8560A(*adapter*, *name='Hewlett-Packard HP8560A'*, ***kwargs*)

Bases: `HP856Xx`

Model the HP 8560A Spectrum Analyzer and expose a high-level interface for instrument interaction.

```python
from pymeasure.instruments.hp import HP8560A
from pymeasure.instruments.hp.hp856Xx import AmplitudeUnits

sa = HP8560A("GPIB::1")

sa.amplitude_unit = AmplitudeUnits.DBUV
sa.start_frequency = 299.5e6
sa.stop_frequency = 300.5e6

print(sa.marker_amplitude)

```
