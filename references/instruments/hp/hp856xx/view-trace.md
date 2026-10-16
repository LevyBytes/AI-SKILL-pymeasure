# pymeasure.instruments.hp.hp856Xx.HP856Xx.view_trace

HP856Xx.view_trace(*trace*)

Show the stored contents of the selected trace without refreshing that trace. View mode can run before a sweep finishes when `sweep_single()` and `trigger_sweep()` are not being used.

Parameters:

**trace** (*str*) – Trace selector; provide a `Trace` value, or use ‘TRA’ for Trace A or ‘TRB’ for Trace B

Raises:

- **TypeError** – Type isn’t ‘string’

- **ValueError** – Raised when the value is neither ‘TRA’ nor ‘TRB’
