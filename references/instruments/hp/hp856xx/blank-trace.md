# pymeasure.instruments.hp.hp856Xx.HP856Xx.blank_trace

HP856Xx.blank_trace(*trace*)

Remove the selected trace from the display. Its existing data remains stored in the trace, but the trace is not updated.

```python
instr.blank_trace('TRA')
instr.blank_trace(Trace.A)

```

Parameters:

**trace** (*str*) – Trace selector; provide a `Trace` value, or use ‘TRA’ for Trace A or ‘TRB’ for Trace B

Raises:

- **TypeError** – Type isn’t ‘string’

- **ValueError** – Raised when the value is neither ‘TRA’ nor ‘TRB’
