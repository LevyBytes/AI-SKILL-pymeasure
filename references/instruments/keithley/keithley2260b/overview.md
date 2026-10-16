# pymeasure.instruments.keithley.Keithley2260B

*class *pymeasure.instruments.keithley.Keithley2260B(*adapter*, *name='Keithley 2260B DC Power Supply'*, *read_termination='\n'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the Keithley 2260B Power Supply with a minimal implementation and exposes a high-level interface for instrument operations.

For tcpip access, use the fixed port 2268; the device does not allow that port to be changed. Use ‘TCPIP::xxx.xxx.xxx.xxx::2268::SOCKET’ as the example connection string. For this interface, read termination is

```python
from pymeasure.instruments.keithley.keithley2260B import Keithley2260B

source = Keithley2260B("GPIB::1")
source.voltage = 1
print(source.voltage)
print(source.current)
print(source.power)
print(source.applied)

```
