# pymeasure.instruments.hp.hp856Xx.HP856Xx.save_trace

HP856Xx.save_trace(*trace*, *number*)

Store the selected trace in the requested trace register.

Parameters:

- **trace** (*str*) – Trace selector; provide a `Trace` value, or use ‘TRA’ for Trace A or ‘TRB’ for Trace B

- **number** (*int*) – Trace storage register, from 0 … 7

```python
instr.preset()
instr.center_frequency = 300e6
instr.span = 20e6

instr.save_trace(Trace.A, 7)
instr.preset()

# reload - at 7 stored trace - to Trace B
instr.recall_trace(Trace.B, 7)

```
