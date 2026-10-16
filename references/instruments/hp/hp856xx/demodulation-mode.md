# pymeasure.instruments.hp.hp856Xx.HP856Xx.demodulation_mode

HP856Xx.demodulation_mode

Set the spectrum analyzer demodulation mode to AM, FM, or off. Put a marker on the target signal, then set `demodulation_mode`; demodulation uses that signal. If no marker is present, `demodulation_mode` places one at the trace center and demodulates the frequency at that marker position. Adjust listening with the volume and squelch controls.

Type: `str`

Accepts a demodulation mode value from `DemodulationMode`, or one of ‘OFF’, ‘AM’, ‘FM’.

```python
from pymeasure.instruments.hp.hp856Xx import DemodulationMode

instr.demodulation_mode = 'AC'
instr.demodulation_mode = DemodulationMode.AM

if instr.demodulation_mode == DemodulationMode.FM:
    instr.demodulation_mode = Demodulation.OFF

```
