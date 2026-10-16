# pymeasure.instruments.hp.hp856Xx.HP856Xx.normalized_reference_position

HP856Xx.normalized_reference_position

Control the normalized reference-position on the graticule where the measured-versus-calibrated trace difference is placed. Its dB value matches the normalized reference level. The normalized reference-position can be set from 0.0 to 10.0, corresponding respectively to the bottom and top graticule lines.

Type: `float`

```python
instr.normalized_reference_position = 5.5

if instr.normalized_reference_position == 5.5:
    pass

```
