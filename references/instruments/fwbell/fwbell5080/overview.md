# pymeasure.instruments.fwbell.FWBell5080

*class *pymeasure.instruments.fwbell.FWBell5080(*adapter*, *name='F.W. Bell 5080 Handheld Gaussmeter'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Model for the F.W. Bell 5080 Handheld Gaussmeter, exposing a high-level interface to the instrument.

Parameters:

**port** – Serial port connected to the instrument

```python
from pymeasure.instruments.fwbell.fwbell5080 import FWBell5080

meter = FWBell5080('/dev/ttyUSB0')  # Connects over serial port /dev/ttyUSB0 (Linux)

meter.units = 'gauss'               # Sets the measurement units to Gauss
meter.range = 1                     # Sets the range to 3 kG
print(meter.field)                  # Reads and prints a field measurement in G

fields = meter.fields(100)          # Samples 100 field measurements
print(fields.mean(), fields.std())  # Prints the mean and standard deviation of the samples

```
