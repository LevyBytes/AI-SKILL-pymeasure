# pymeasure.instruments.hp.hp856Xx.HP856Xx.squelch

HP856Xx.squelch

Set the demodulation squelch level. When enabled, the display shows a dashed line for the squelch level. Demodulation requires an active marker above that line. See the `demodulation_mode` command. The default value is -120 dBm.

Type: `str,int`

```python
from pymeasure.instruments.hp.hp856Xx import DemodulationMode, PeakSearchMode

instr.preset()
instr.start_frequency = 88e6
instr.stop_frequency = 108e6

instr.peak_search(PeakSearchMode.High)
instr.demodulation_time = 10

instr.squelch = -60
instr.demodulation_mode = DemodulationMode.FM

```
