# pymeasure.instruments.hp.hp856Xx.HP856Xx.frequency_reference_source

HP856Xx.frequency_reference_source

Set the frequency reference source. Use the internal frequency reference (INT), or provide an external reference (EXT). The external reference must be 10 MHz (+100 Hz) with minimum amplitude 0 dBm. Connect it to J9 (10 MHz REF IN/OUT) on the rear panel. In external mode, an “X” appears at the left edge of the display.

Type: `str`

Accepts an element of `FrequencyReference`, or the literal ‘INT’ or ‘EXT’.

```python
from pymeasure.instruments.hp.hp856Xx import FrequencyReference

instr.frequency_reference_source = 'INT'
instr.frequency_reference_source = FrequencyReference.EXT

if instr.frequency_reference_source == FrequencyReference.INT:
    instr.frequency_reference_source = FrequencyReference.EXT

```
