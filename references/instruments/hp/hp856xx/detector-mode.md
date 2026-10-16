# pymeasure.instruments.hp.hp856Xx.HP856Xx.detector_mode

HP856Xx.detector_mode

Choose the IF detector for measurement acquisition. In coupled operation the spectrum analyzer normally selects the suitable detector mode. The four detector modes are normal, positive, negative, and sample.

Type: `str`

Accepts a detector mode value, either from `DetectionModes` or one of ‘NEG’, ‘NRM’, ‘POS’, ‘SMP’.

```python
from pymeasure.instruments.hp.hp856Xx import DetectionModes

instr.detector_mode = DetectionModes.SMP
instr.detector_mode = 'NEG'

if instr.detector_mode == DetectionModes.SMP:
    pass

```
