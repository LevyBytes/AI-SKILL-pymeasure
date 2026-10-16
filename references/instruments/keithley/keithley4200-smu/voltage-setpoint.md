# pymeasure.instruments.keithley.keithley4200.SMU.voltage_setpoint

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *voltage_setpoint*: Any*

Configure range, output voltage, and current compliance (int, float, float).

Voltage uses Volts and current uses Amps.

```python
from pymeasure.instruments.keithley.keithley4200 import Keithley4200

inst = Keithley4200("TCPIP::192.168.1.1::1225::SOCKET")
inst.smu1.voltage_setpoint = (0, 3.3, 1e-2)  # (range, value, compliance)
# Set SMU1 to output 3.3 V in autorange with 10 mA current compliance

```

Voltage source range:

- 0: autorange

- 1: 20 V range

- 2: 200 V range

- 3: 200 V range

- 4: 200 mV range; requires a preamplifier

- 5: 2 V range; requires a preamplifier
