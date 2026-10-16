# pymeasure.instruments.hp.hp856Xx.HP856Xx.normalized_reference_level

HP856Xx.normalized_reference_level

Control the normalized reference level for use with the `normalize_trace_data` command. Using ‘normalized_reference_level’ does not change the input attenuator or IF step gains. It acts as a trace-offset function, letting the displayed trace be shifted without adding hardware-switching errors to the stimulus-response measurement. The unit for ‘normalized_reference_level’ is dB. In absolute power mode (dBm), reference level (`reference_level`) changes instrument gain and RF attenuation settings, which affects measurement or dynamic range. In normalized mode, meaning relative power or dB-measurement mode, NRL offsets on-screen trace data without changing gain or attenuation. This lets the normalized trace move on the display without reducing measurement accuracy through gain or RF attenuation changes. If the measurement range must be changed to put trace data on-screen, adjust the range level. In normalized mode, changing the range level affects instrument settings the same way reference level does in absolute power mode when normalize is off.

Type: `int`

```python
# reference level in case of normalization to -30 DB
instr.normalized_reference_level = -30

if instr.normalized_reference_level == -30:
    pass

```
