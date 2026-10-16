# pymeasure.instruments.hp.hp856Xx.HP856Xx.start_frequency

HP856Xx.start_frequency

Set the start frequency and put the spectrum analyzer in start-frequency/ stop-frequency mode. If start frequency is higher than stop frequency, stop frequency is raised to start frequency plus 100 Hz. Changes to start frequency also update center frequency and span.

Type: `float`

```python
instr.start_frequency = 300.5e6
if instr.start_frequency == 200e3:
    print("Correct frequency")

```

(dynamic)
