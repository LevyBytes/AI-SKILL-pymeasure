# pymeasure.instruments.keithley.Keithley2450.measure_resistance

[Owning PyMeasure class, adapter and connection contract](overview.md)

measure_resistance(*nplc=1*, *resistance=210000.0*, *auto_range=True*)

Configures the measurement of resistance.

Parameters:

- **nplc** - Power line cycle count (NPLC) for resistance measurements, from 0.01 to 10 (default: `1`)

- **resistance** - Resistance upper limit in Ohms, from -210 MOhms to 210 MOhms (default: `210000.0`)

- **auto_range** - If True, enables auto_range; otherwise the set resistance is used (default: `True`)
