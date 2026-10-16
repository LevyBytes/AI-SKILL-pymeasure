# pymeasure.instruments.keithley.Keithley2400Legacy

*class *pymeasure.instruments.keithley.Keithley2400Legacy(*adapter*, *name='Keithley 2400 SourceMeter'*, ***kwargs*)

Bases: `KeithleyBuffer`, [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Model the Keithley 2400 SourceMeter and expose a high-level interface for instrument interaction.

Deprecated since version 0.16: This legacy Keithley2400 implementation is frozen at PyMeausure version 0.15 and retained for backwards compatibility.

```python
from pymeasure.instruments.keithley import Keithley2400Legacy

keithley = Keithley2400Legacy("GPIB::1")

keithley.apply_current()                # Sets up to source current
keithley.source_current_range = 10e-3   # Sets the source current range to 10 mA
keithley.compliance_voltage = 10        # Sets the compliance voltage to 10 V
keithley.source_current = 0             # Sets the source current to 0 mA
keithley.enable_source()                # Enables the source output

keithley.measure_voltage()              # Sets up to measure voltage

keithley.ramp_to_current(5e-3)          # Ramps the current to 5 mA
print(keithley.voltage)                 # Prints the voltage in Volts

keithley.shutdown()                     # Ramps the current to 0 mA and disables output

```
