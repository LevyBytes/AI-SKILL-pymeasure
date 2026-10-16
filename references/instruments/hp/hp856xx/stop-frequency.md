# pymeasure.instruments.hp.hp856Xx.HP856Xx.stop_frequency

HP856Xx.stop_frequency

Set the stop frequency and put the spectrum analyzer in start-frequency/ stop-frequency mode. If stop frequency is below start frequency, start frequency is reduced to stop frequency minus 100 Hz. Changes to stop frequency also update center frequency and span.

Type: `float`

```python
instr.stop_frequency = 300.5e6
if instr.stop_frequency == 200e3:
    print("Correct frequency")

```

(dynamic)
