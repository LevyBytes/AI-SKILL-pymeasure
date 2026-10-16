# pymeasure.instruments.hp.hp856Xx.HP856Xx.peak_excursion

HP856Xx.peak_excursion

Define the trace behavior that qualifies as a peak. The selected value is the required monotonic rise followed by monotonic fall for a candidate to count as a peak.
For example, with peak excursion at 10 dB, both sides of the candidate must drop at least 10 dB before it is counted; see Figure 5-4.
The default value is 6 dB.
In linear mode, enter marker peak excursion as a unit-less number. Portions of a peak below the peak threshold also count toward the peak excursion requirement. For example, with peak excursion at 6 dB, a peak 3 dB above the threshold is detected when it continues at least 3 dB more below the threshold level.

Type: `float`

```python
instr.peak_excursion = 2
if instr.peak_excursion == 2:
    pass

```
