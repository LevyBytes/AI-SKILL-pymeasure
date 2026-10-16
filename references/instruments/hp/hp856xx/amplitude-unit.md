# pymeasure.instruments.hp.hp856Xx.HP856Xx.amplitude_unit

HP856Xx.amplitude_unit

Select the amplitude unit from string values ‘DBM’, ‘DBMV’, ‘DBUV’, ‘V’, ‘W’, ‘AUTO’, ‘MAN’, or from enum `AmplitudeUnits`.

Type: `str`

```python
from pymeasure.instruments.hp.hp856Xx import AmplitudeUnits

instr.amplitude_unit = 'dBmV'
instr.amplitude_unit = AmplitudeUnits.dBmV

```
