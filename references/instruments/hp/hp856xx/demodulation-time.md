# pymeasure.instruments.hp.hp856Xx.HP856Xx.demodulation_time

HP856Xx.demodulation_time

Set how long the sweep stops at the marker while demodulating a signal. The default value is 1 second. If the frequency span equals 0 Hz, demodulation continues except between sweeps. For uninterrupted demodulation, use frequency span 0 Hz with trigger mode set to single sweep (see TM). Minimum 100 ms to maximum 60 s.

Type: `float`

```python
# set the demodulation time to 1.2 seconds
instr.demodulation_time = 1.2

if instr.demodulation_time == 10:
    pass

```
