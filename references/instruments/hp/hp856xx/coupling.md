# pymeasure.instruments.hp.hp856Xx.HP856Xx.coupling

HP856Xx.coupling

Set the spectrum analyzer input coupling. AC coupling shields the analyzer input from harmful dc signals, but it limits the lower frequency range to 100 kHz even though the analyzer can tune down to 0 Hz when signal attenuation is applied.

Type: `str`

Accepts a coupling mode value from `CouplingMode`, or the literal ‘AC’ / ‘DC’.

```python
from pymeasure.instruments.hp.hp856Xx import CouplingMode

instr.coupling = 'AC'
instr.coupling = CouplingMode.DC

if instr.coupling == CouplingMode.DC:
    pass

```
