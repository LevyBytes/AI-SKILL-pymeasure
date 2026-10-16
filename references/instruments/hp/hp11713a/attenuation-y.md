# pymeasure.instruments.hp.HP11713A.attenuation_y

[Owning PyMeasure class, adapter and connection contract](overview.md)

attenuation_y(*attenuation*)

Configure the Y switches for the requested attenuation in dB

Requested attenuation is rounded to the next available step. Set an attenuation mapping first, e.g.

```python
from pymeasure.instruments.hp.hp11713a import HP11713A, Attenuator_110dB

instr.ATTENUATOR_Y = Attenuator_110dB
instr.attenuation_y(10)

```
