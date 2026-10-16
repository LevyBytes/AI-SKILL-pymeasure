# pymeasure.instruments.keithley.Keithley2450.measure_current

[Owning PyMeasure class, adapter and connection contract](overview.md)

measure_current(*nplc=1*, *current=0.000105*, *auto_range=True*)

Configures the measurement of current.

Parameters:

- **nplc** - Power line cycle count (NPLC) for current measurements, from 0.01 to 10 (default: `1`)

- **current** - Current upper limit in Amps, from -1.05 A to 1.05 A (default: `0.000105`)

- **auto_range** - If True, enables auto_range; otherwise the set current is used (default: `True`)
