# pymeasure.instruments.hp.hp856Xx.HP856Xx.demodulation_agc_enabled

HP856Xx.demodulation_agc_enabled

Set demodulation automatic gain control (AGC). During AM demodulation, AGC keeps speaker volume comparatively steady. It is available only for AM demodulation when the frequency span is greater than 0 Hz.

Type: `bool`

```python
instr.demodulation_agc = True

if instr.demodulation_agc:
    instr.demodulation_agc = False

```
