# pymeasure.instruments.agilent.agilent4156.SMU.compliance

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *compliance

Set or read SMU&lt;n&gt; *constant* compliance value.

For an SMU channel configured as variable (VAR1, VAR2, VARD), the variable definition supplies compliance limits.

- Value: Voltage in (-200V, 200V) and current in (-1A, 1A), selected according to `channel_mode()`.

```python
instr.smu1.compliance = 0.1

```
