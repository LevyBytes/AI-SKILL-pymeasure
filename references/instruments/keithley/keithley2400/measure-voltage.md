# pymeasure.instruments.keithley.Keithley2400.measure_voltage

[Owning PyMeasure class, adapter and connection contract](overview.md)

measure_voltage(*nplc=1*, *voltage=21.0*, *auto_range=True*)

Configure the measurement of voltage.

Parameters:

- **nplc** — NPLC power-line-cycle setting, from 0.01 to 10 (default: `1`)

- **voltage** — Upper voltage limit in Volts, from -210 V to 210 V (default: `21.0`)

- **auto_range** — Turns on auto_range when True; otherwise uses the supplied voltage (default: `True`)

Deprecated since version 0.16: Voltage measurement setup now happens implicitly through `voltage`. Prefer - voltage nplc through `voltage_nplc`. - voltage range through `voltage_range` or `voltage_range_auto_enabled`.

## Related property contracts

- Open when checking pymeasure.instruments.keithley.Keithley2400.min_current: [min_current](min-current.md).
- Open when checking pymeasure.instruments.keithley.Keithley2400.min_resistance: [min_resistance](min-resistance.md).
- Open when checking pymeasure.instruments.keithley.Keithley2400.min_voltage: [min_voltage](min-voltage.md).
