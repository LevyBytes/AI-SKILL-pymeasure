# pymeasure.instruments.hp.hp856Xx.HP856Xx.marker_delta

HP856Xx.marker_delta

Control a second marker on the trace. The parameter gives the separation between the two markers in frequency, or in time when zero span is active. A query returns the frequency or time of the second marker.

Type: `float`

```python
# place second marker 1 MHz apart from the first marker
instr.marker_delta = 1e6

# print frequency of second marker in case it got moved automatically
print(instr.marker_delta)

```
