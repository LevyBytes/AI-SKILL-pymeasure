# pymeasure.instruments.keithley.Keithley2400.measure_resistance

[Owning PyMeasure class, adapter and connection contract](overview.md)

measure_resistance(*nplc=1*, *resistance=210000.0*, *auto_range=True*)

Configure the measurement of resistance.

Parameters:

- **nplc** — NPLC power-line-cycle setting, from 0.01 to 10 (default: `1`)

- **resistance** — Upper resistance limit in Ohms, from -210 MOhms to 210 MOhms (default: `210000.0`)

- **auto_range** — Turns on auto_range when True; otherwise uses the supplied resistance (default: `True`)

Deprecated since version 0.16: Resistance measurement setup now happens implicitly through `resistance`. Instead: - set resistance nplc with `resistance_nplc`. - set resistance range with `resistance_range` or `resistance_range_auto_enabled`.
