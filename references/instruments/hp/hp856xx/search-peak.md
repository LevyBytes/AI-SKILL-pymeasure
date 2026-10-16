# pymeasure.instruments.hp.hp856Xx.HP856Xx.search_peak

HP856Xx.search_peak(*mode*)

Place a marker at a trace peak: the highest point, the next-highest point, the next peak to the left, or the next peak to the right. The default mode is ‘HI’. A trace peak is found only when it satisfies the marker threshold and peak excursion requirements. See the `peak_threshold` and `peak_excursion` commands as well.

Parameters:

**mode** (*str*) – Accepts ‘HI’, ‘NH’, ‘NR’, ‘NL’, or a `PeakSearchMode` enumeration member

```python
from pymeasure.instruments.hp.hp856Xx import PeakSearchMode

instr.search_peak('NL')
instr.search_peak(PeakSearchMode.NextHigh)

```
