# pymeasure.instruments.keithley.Keithley2400Legacy.measure_voltage

[Owning PyMeasure class, adapter and connection contract](overview.md)

measure_voltage(*nplc=1*, *voltage=21.0*, *auto_range=True*)

Configure the measurement of voltage.

Parameters:

- **nplc** - number of power line cycles (NPLC), from 0.01 through 10 (default: `1`)

- **voltage** - upper voltage limit in Volts, from -210 V to 210 V (default: `21.0`)

- **auto_range** - enables auto_range when True; otherwise uses the set voltage (default: `True`)

## Related property contracts

- Open when checking pymeasure.instruments.keithley.Keithley2400Legacy.min_current: [min_current](min-current.md).
- Open when checking pymeasure.instruments.keithley.Keithley2400Legacy.min_resistance: [min_resistance](min-resistance.md).
- Open when checking pymeasure.instruments.keithley.Keithley2400Legacy.min_voltage: [min_voltage](min-voltage.md).
