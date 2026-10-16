# pymeasure.instruments.keithley.Keithley2281S

*class *pymeasure.instruments.keithley.Keithley2281S(*adapter*, *name='Keithley2281S'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument), `KeithleyBuffer`

Models the Keithley 2281S-20-6 power supply and battery simulator / characterizer as an instrument class. Common commands other than function_mode and power supply commands are expected to operate on Keithley 2280S power supplies as well, but that has not been tested.
