# pymeasure.instruments.texio.TexioPSW360L30

*class *pymeasure.instruments.texio.TexioPSW360L30(*adapter*, *name='TEXIO PSW-360L30 Power Supply'*, ***kwargs*)

Bases: [`Keithley2260B`](https://pymeasure.readthedocs.io/en/latest/api/instruments/keithley/keithley2260B.html#pymeasure.instruments.keithley.Keithley2260B)

Provides a minimal TEXIO PSW-360L30 Power Supply representation and a high-level interface for instrument operations.

When using tcpip, this device listens only on port 2268; that port is not configurable. example connection string: ?TCPIP::xxx.xxx.xxx.xxx::2268::SOCKET?

On Linux USB connections, the kernel automatically creates a /dev/ttyACMX device. The serial settings are fixed at 9600?8-N-1.

This interface terminates reads with Line-Feed n.

This driver derives from the Keithley2260B implementation, so every instruction supported by the Keithley 2260B driver is available on the TEXIO PSW-360L30 power supply.

It adds only the ?output? property, an alias for the Keithley 2260B ?enabled? property. The name ?enabled? can be ambiguous because it does not say whether it affects the whole device or just the output.

```python
from pymeasure.instruments.texio.texioPSW360L30 import TexioPSW360L30

source = TexioPSW360L30("TCPIP::xxx.xxx.xxx.xxx::2268::SOCKET")
source.voltage = 1
print(source.voltage)
print(source.current)
print(source.power)
print(source.applied)

```
