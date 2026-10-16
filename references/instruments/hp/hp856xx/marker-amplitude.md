# pymeasure.instruments.hp.hp856Xx.HP856Xx.marker_amplitude

HP856Xx.marker_amplitude

Read the active marker amplitude. If no marker is currently active, MKA creates a marker at the trace center and returns that amplitude in the unit selected by `amplitude_unit()`.

Type: `float`

```python
level = instr.marker_amplitude
unit = instr.amplitude_unit
print("Level: %f %s" % (level, unit))

```
