# pymeasure.instruments.keithley.Keithley6517B

*class *pymeasure.instruments.keithley.Keithley6517B(*adapter*, *name='Keithley 6517B Electrometer/High Resistance Meter'*, ***kwargs*)

Bases: `KeithleyBuffer`, [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the Keithley 6517B ElectroMeter, exposing a higher-level API for instrument operations.

```python
from pymeasure.instruments.keithley.keithley6517b import Keithley6517B

keithley = Keithley6517B("GPIB::1")

keithley.apply_voltage()              # Sets up to source voltage
keithley.source_voltage_range = 200   # Sets the source voltage
                                      # range to 200 V
keithley.source_voltage = 20          # Sets the source voltage to 20 V
keithley.enable_source()              # Enables the source output

keithley.measure_resistance()         # Sets up to measure resistance

keithley.ramp_to_voltage(50)          # Ramps the voltage to 50 V
print(keithley.resistance)            # Prints the resistance in Ohms

keithley.shutdown()                   # Ramps the voltage to 0 V
                                      # and disables output

```
