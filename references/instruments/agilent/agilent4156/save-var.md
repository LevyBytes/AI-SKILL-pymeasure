# pymeasure.instruments.agilent.agilent4156.Agilent4156.save_var

[Owning PyMeasure class, adapter and connection contract](overview.md)

save_var(*trace_list*)

Store voltage or current in the instrument variable list.

Use this when saving one or two additional variables beyond the 8 variables permitted by `save()`.

Parameters:

**trace_list** — Channel-variable list whose measured data should be saved. Up to 2 variables are allowed. When saving a single variable, a string may be used.

```python
instr.save_var(['VA', 'VB'])

```
