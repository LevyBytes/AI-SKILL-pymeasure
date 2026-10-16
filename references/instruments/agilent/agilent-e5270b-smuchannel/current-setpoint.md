# pymeasure.instruments.agilent.agilentE5270B.SMUChannel.current_setpoint

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *current_setpoint*: Any*

Configure range, output current, and voltage compliance (int, float, float).

```python
from pymeasure.instruments.agilent.agilentE5270B import AgilentE5270B

inst = AgilentE5270B("GPIB0::17::INSTR")
inst.smu1.current_setpoint = (0, 1.32e-3, 0.5)  # (range, value, compliance)
# Set SMU1 to output 1.32 mA in autorange with 0.5 V voltage compliance

```

Ranges:

- `0`: Auto ranging

- `8`: limited auto ranging at 1 pA for E5287A+E5288A

- `9`: limited auto ranging at 10 pA for E5287A

- `10`: limited auto ranging at 100 pA for E5287A

- `11`: 1 nA limited auto ranging

- `12`: 10 nA limited auto ranging

- `13`: 100 nA limited auto ranging

- `14`: 1 μA limited auto ranging

- `15`: 10 μA limited auto ranging

- `16`: 100 μA limited auto ranging

- `17`: 1 mA limited auto ranging

- `18`: 10 mA limited auto ranging

- `19`: 100 mA limited auto ranging

- `20`: limited auto ranging at 1 A for E5280B
