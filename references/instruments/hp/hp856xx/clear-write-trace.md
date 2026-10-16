# pymeasure.instruments.hp.hp856Xx.HP856Xx.clear_write_trace

HP856Xx.clear_write_trace(*trace*)

Put the selected trace into clear-write mode. The mode first sets every element of that trace to the bottom-screen value, then each sweep writes fresh detector data into the trace.

```python
instr.clear_write_trace('TRA')
instr.clear_write_trace(Trace.A)

```

Parameters:

**trace** (*str*) – Trace selector; provide a `Trace` value, or use ‘TRA’ for Trace A or ‘TRB’ for Trace B

Raises:

- **TypeError** – Type isn’t ‘string’

- **ValueError** – Raised when the value is neither ‘TRA’ nor ‘TRB’
