# pymeasure.instruments.agilent.agilent4156.SMU.current_name

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *current_name*: Any*

Set or read the channel current name.

When input exceeds 6 characters or begins with a number, the name is corrected automatically by prefixing ?a?; the event is logged.

```python
instr.smu1.voltage_name = "Vbase"

```
