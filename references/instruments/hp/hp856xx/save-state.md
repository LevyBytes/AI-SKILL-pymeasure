# pymeasure.instruments.hp.hp856Xx.HP856Xx.save_state

HP856Xx.save_state(*inp*)

Store the instrument state currently shown on the display into the specified state register.

Parameters:

- **inp** – State selection to recall: storage slot 0 … 9, ‘LAST’, or ‘PWRON’

- **inp** – str, int

```python
instr.preset()
instr.center_frequency = 300e6
instr.span = 20e6
instr.save_state("PWRON")

```
