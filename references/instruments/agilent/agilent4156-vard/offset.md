# pymeasure.instruments.agilent.agilent4156.VARD.offset

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *offset

Set or read VARD OFFSET value. At each sweep step, VAR1? output values follow this equation: VARD = VAR1 X RATio + OFFSet. Use this command only when an SMU or VSU function is VARD.

```python
instr.vard.offset = 1

```
