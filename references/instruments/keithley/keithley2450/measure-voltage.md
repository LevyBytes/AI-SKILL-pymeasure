# pymeasure.instruments.keithley.Keithley2450.measure_voltage

[Owning PyMeasure class, adapter and connection contract](overview.md)

measure_voltage(*nplc=1*, *voltage=21.0*, *auto_range=True*)

Configures the measurement of voltage.

Parameters:

- **nplc** - Power line cycle count (NPLC) for voltage measurements, from 0.01 to 10 (default: `1`)

- **voltage** - Voltage upper limit in Volts, from -210 V to 210 V (default: `21.0`)

- **auto_range** - If True, enables auto_range; otherwise the set voltage is used (default: `True`)

## Related property contracts

- Open when checking pymeasure.instruments.keithley.Keithley2450.min_current: [min_current](min-current.md).
- Open when checking pymeasure.instruments.keithley.Keithley2450.min_resistance: [min_resistance](min-resistance.md).
- Open when checking pymeasure.instruments.keithley.Keithley2450.min_voltage: [min_voltage](min-voltage.md).
