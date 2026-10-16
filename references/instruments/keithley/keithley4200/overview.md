# pymeasure.instruments.keithley.Keithley4200

Class signature: *class *pymeasure.instruments.keithley.Keithley4200(*adapter*, *name='Keithley 4200A-SCS'*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Class for the Keithley 4200A-SCS Parameter Analyzer.

This driver controls the SMUs using only user mode commands.

Run the ‘KXCI’ program on the 4200A-SCS before remote control. Configure the remote interface with the Keithley Configuration Utility ‘KCon’.

At present, the driver works only with the ethernet interface.
