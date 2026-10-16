# pymeasure.instruments.hp.hp856Xx.HP856Xx.recall_state

HP856Xx.recall_state(*inp*)

Recall a previously saved instrument state onto the display. See `save_state()`.

Parameters:

- **inp** – State selection to recall: storage slot 0 … 9, ‘LAST’, or ‘PWRON’

- **inp** – str, int

```python
instr.save_state(7)
instr.preset()
instr.recall_state(7)

```
