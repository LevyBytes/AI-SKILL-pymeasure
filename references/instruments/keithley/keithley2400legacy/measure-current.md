# pymeasure.instruments.keithley.Keithley2400Legacy.measure_current

[Owning PyMeasure class, adapter and connection contract](overview.md)

measure_current(*nplc=1*, *current=0.000105*, *auto_range=True*)

Configure the measurement of current.

Parameters:

- **nplc** - number of power line cycles (NPLC), from 0.01 through 10 (default: `1`)

- **current** - upper current limit in Amps, from -1.05 A to 1.05 A (default: `0.000105`)

- **auto_range** - enables auto_range when True; otherwise uses the set current (default: `True`)
