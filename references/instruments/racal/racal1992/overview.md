# pymeasure.instruments.racal.Racal1992

*class *pymeasure.instruments.racal.Racal1992(*adapter*, *name='Racal-Dana 1992'*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Represents a Racal-Dana 1992 Universal counter

```python
from pymeasure.instruments.racal import Racal1992
counter = Racal1992("GPIB0::10")

```

This class should also support Racal-Dana 1991 because it uses the same product manual, provided you avoid features that need channel B.
