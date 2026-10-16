# pymeasure.instruments.hp.hp856Xx.HP856Xx.frequency_offset

HP856Xx.frequency_offset

Set an offset added to displayed absolute-frequency values, including marker-frequency values.

The offset leaves the sweep frequency range unchanged and does not alter relative frequency readouts. When enabled, an “F” is shown on the left side of the display. It changes all of the following frequency measurements.

Type: `float`

```python
instr.frequency_offset = 2e6
if instr.frequency_offset == 2e6:
    print("Correct frequency")

```

(dynamic)
