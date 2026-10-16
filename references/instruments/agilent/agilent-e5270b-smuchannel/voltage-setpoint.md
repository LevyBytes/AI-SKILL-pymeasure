# pymeasure.instruments.agilent.agilentE5270B.SMUChannel.voltage_setpoint

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *voltage_setpoint*: Any*

Configure range, output voltage, and current compliance (int, float, float)

```python
from pymeasure.instruments.agilent.agilentE5270B import AgilentE5270B

inst = AgilentE5270B("GPIB0::17::INSTR")
inst.smu1.voltage_setpoint = (12, 14.42, 0.05)  # (range, value, compliance)
# Set SMU1 to output 14.42 V in 20 V range with 50 mA current compliance

```

Ranges:

- `0`: Auto ranging

- `5`: limited auto ranging at 0.5 V for E5281B/E5287A

- `50`: limited auto ranging at 5 V for E5281B/E5287A

- `11` or `20`: 2 V limited auto ranging

- `12` or `200`: 20 V limited auto ranging

- `13` or `400`: 40 V limited auto ranging

- `14` or `1000`: 100 V limited auto ranging

- `15` or `2000`: limited auto ranging at 200 V for E5280B
