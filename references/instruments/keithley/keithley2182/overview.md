# pymeasure.instruments.keithley.Keithley2182

Covers: Keithley 2182 Nanovoltmeter; Keithley 2700 MultiMeter/Switch System.

## Keithley 2182 Nanovoltmeter

### Keithley 2182 Nanovoltmeter

 *class *pymeasure.instruments.keithley.Keithley2182(*adapter*, *name='Keithley 2182 Nanovoltmeter'*, *read_termination='\r'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), `KeithleyBuffer`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Model interface for the Keithley 2182 Nanovoltmeter, exposing high-level operations for communicating with the instrument.

```python
from pymeasure.instruments.keithley import Keithley2182

keithley = Keithley2182("GPIB::1")

keithley.reset()                        # Return instrument settings to default
                                          # values
keithley.thermocouple = 'S'             # Sets thermocouple type to S
keithley.active_channel = 1             # Sets channel 1 for active measurement
keithley.channel_function = 'voltage'   # Configures active channel for voltage
                                          # measurement
print(keithley.voltage)                 # Prints the voltage in volts

keithley.ch_1.setup_voltage()           # Set channel 1 active and prepare
                                          # voltage measurement
keithley.ch_2.setup_temperature()       # Set channel 2 active and prepare
                                          # temperature measurement

```
