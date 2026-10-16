# pymeasure.instruments.keithley.Keithley2400

*class *pymeasure.instruments.keithley.Keithley2400(*adapter*, *name='Keithley 2400 SourceMeter'*, ***kwargs*)

Bases: `KeithleyBuffer`, [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Model the Keithley 2400 SourceMeter and expose a high-level interface for instrument communication.

```python
from pymeasure.instruments.keithley.keithley2400 import Keithley2400

smu = Keithley2400("GPIB::1")
smu.reset()                        # Resets the instrument

smu.source_mode = "current"        # Sets up to source current
smu.source_enabled = True          # Enables the source output

smu.ramp_to_current(5e-3)          # Ramps the current to 5 mA
print(smu.voltage)                 # Prints the voltage in Volts

smu.reset()                        # Resets the instrument

```
