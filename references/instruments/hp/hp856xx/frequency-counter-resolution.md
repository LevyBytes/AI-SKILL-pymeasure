# pymeasure.instruments.hp.hp856Xx.HP856Xx.frequency_counter_resolution

HP856Xx.frequency_counter_resolution

Set the frequency counter resolution. See the ‘frequency_counter_mode’ command. The default value is 10 kHz.

Type `int`
```python
# activate frequency counter mode
instr.frequency_counter_mode = True

# adjust resolution to 1 Hz
instr.frequency_counter_resolution = 1

if instr.frequency_counter_resolution:
    pass

```
