# pymeasure.instruments.keithley.keithley4200.SMU.current_setpoint

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *current_setpoint*: Any*

Configure range, output current, and voltage compliance (int, float, float).

Current uses Amps and voltage uses Volts.

```python
from pymeasure.instruments.keithley.keithley4200 import Keithley4200

inst = Keithley4200("TCPIP::192.168.1.1::1225::SOCKET")
inst.smu1.current_setpoint = (9, 55e-3, 10)  # (range, value, compliance)
# Set SMU1 to output 55 mA in 100 mA range with 10 V voltage compliance

```

Current source range:

- 0: autorange

- 1: 1 nA range; requires a preamplifier

- 2: 10 nA range; requires a preamplifier

- 3: 100 nA range

- 4: 1 µA range

- 5: 10 µA range

- 6: 100 µA range

- 7: 1 mA range

- 8: 10 mA range

- 9: 100 mA range

- 10: 1 A range; requires a 4210-SMU or 4211-SMU

- 11: 1 pA range; requires a preamplifier

- 12: 10 pA range; requires a preamplifier

- 13: 100 pA range; requires a preamplifier
