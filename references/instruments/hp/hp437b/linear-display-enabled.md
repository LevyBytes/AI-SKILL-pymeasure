# pymeasure.instruments.hp.HP437B.linear_display_enabled

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *linear_display_enabled*: Any*

Controls whether displayed or reported power values use logarithmic or linear units. Set linear_display_enabled to `True` to enable linear readout.

```python
from pymeasure.instruments.hp.hp437b import LogLin

instr.relative_mode_enabled = False
instr.linear_display_enabled = True

```
