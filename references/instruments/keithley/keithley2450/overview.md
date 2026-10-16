# pymeasure.instruments.keithley.Keithley2450

*class *pymeasure.instruments.keithley.Keithley2450(*adapter*, *name='Keithley 2450 SourceMeter'*, ***kwargs*)

Bases: `KeithleyBuffer`, [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the Keithley 2450 SourceMeter and exposes a high-level control interface for that instrument.

NOTE: PyMeasure does not currently support the Keithley 2450 model's default buffer-handling SCPI command set. Operation works when the instrument is configured to emulate a 2400 model by selecting 'SCPI 2400' as the command set in the instrument's system settings.

```python
from pymeasure.instruments.keithley.keithley2450 import Keithley2450

keithley = Keithley2450("GPIB::1")

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
