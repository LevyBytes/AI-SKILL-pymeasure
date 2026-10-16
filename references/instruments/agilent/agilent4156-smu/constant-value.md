# pymeasure.instruments.agilent.agilent4156.SMU.constant_value

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *constant_value

Set or read SMU&lt;n&gt; constant source value.

Use this command only when `channel_function()` is `CONS` and `channel_mode()` is not `COMM`.

Parameters:

**const_value** — Voltage in (-200V, 200V) and current in (-1A, 1A). Whether voltage or current applies depends on `channel_mode()` being `V` or `I`.

```python
instr.smu1.constant_value = 1

```
