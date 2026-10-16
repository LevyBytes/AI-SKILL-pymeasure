# pymeasure.instruments.agilent.agilent4156.Agilent4156.save

[Owning PyMeasure class, adapter and connection contract](overview.md)

save(*trace_list*)

Store voltage or current in the instrument display list.

Parameters:

**trace_list** — Channel-variable list whose measured data should be saved. Up to 8 variables are allowed. When saving a single variable, a string may be used.

```python
instr.save(['IC', 'IB', 'VC', 'VB']) #for list of variables
instr.save('IC')    #for single variable

```
