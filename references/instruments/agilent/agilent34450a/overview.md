# pymeasure.instruments.agilent.Agilent34450A

Scope includes the HP/Agilent/Keysight 34450A Digital Multimeter, the Agilent 4294A Precision Impedance Analyzer, the Agilent 33220A Arbitrary Waveform Generator, and the Agilent 8722ES Vector Network Analyzer.

## HP/Agilent/Keysight 34450A Digital Multimeter

### HP/Agilent/Keysight 34450A Digital Multimeter

Class constructor: pymeasure.instruments.agilent.Agilent34450A(adapter, name='HP/Agilent/Keysight 34450A Multimeter', **kwargs).

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Python interface for the HP/Agilent/Keysight 34450A and related multimeters.

```python
from pymeasure.instruments.agilent.agilent34450A import Agilent34450A

dmm = Agilent34450A("USB0::...")
dmm.reset()
dmm.configure_voltage()
print(dmm.voltage)
dmm.shutdown()

```
