# pymeasure.instruments.hp.hp856Xx.HP856Xx.center_frequency

HP856Xx.center_frequency

Set the center frequency in hertz and switch the spectrum analyzer to center frequency / span mode.

Span stays fixed; start and stop frequencies move when center frequency changes.

Type: `float`

```python
instr.center_frequency = 300.5e6
if instr.center_frequency == 200e3:
    print("Correct frequency")

```

(dynamic)
