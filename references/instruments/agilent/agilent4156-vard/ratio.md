# pymeasure.instruments.agilent.agilent4156.VARD.ratio

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *ratio*: Any*

Set or read RATIO of VAR1?. At each sweep step, VAR1? output values follow this equation: VAR1? = VAR1 * RATio + OFFSet. Use this command only when an SMU or VSU function (FCTN) is VAR1?.

```python
instr.vard.ratio = 1

```
