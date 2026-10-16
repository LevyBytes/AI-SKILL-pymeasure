# pymeasure.instruments.keithley.Keithley2400Legacy.measure_resistance

[Owning PyMeasure class, adapter and connection contract](overview.md)

measure_resistance(*nplc=1*, *resistance=210000.0*, *auto_range=True*)

Configure the measurement of resistance.

Parameters:

- **nplc** - number of power line cycles (NPLC), from 0.01 through 10 (default: `1`)

- **resistance** - upper resistance limit in Ohms, from -210 MOhms to 210 MOhms (default: `210000.0`)

- **auto_range** - enables auto_range when True; otherwise uses the set resistance (default: `True`)
