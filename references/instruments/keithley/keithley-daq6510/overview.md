# pymeasure.instruments.keithley.KeithleyDAQ6510

*class *pymeasure.instruments.keithley.KeithleyDAQ6510(*adapter*, *name='Keithley DAQ6510'*, ***kwargs*)

Bases: `KeithleyBuffer`, [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the Keithley DAQ6510 Data Acquisition Logging Multimeter System and exposes a high-level interface for instrument interaction.

```python
from pymeasure.instruments.keithley.keithleyDAQ6510 import KeithleyDAQ6510

keithley = KeithleyDAQ6510("GPIB::1")
keithley = KeithleyDAQ6510("TCPIP::192.168.1.1::INSTR")

print(keithley.current)                 # Prints the current in Amps
keithley.current_range = 10E-6          # Select the 10 uA range

print(keithley.voltage)                 # Prints the voltage in Volts
keithley.voltage_range = 100e-3         # Select the 100 mV range

print(keithley.resistance)              # Prints the resistance in Ohms
keithley.offset_compensated = "ON"      # Turns offset-compensated ohms on

keithley.open_channels([134, 135])      # Open channels 134 and 135 on the MUX card
keithley.close_channel(133)             # Close channel 133 on the MUX card

```
