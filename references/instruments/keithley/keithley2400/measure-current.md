# pymeasure.instruments.keithley.Keithley2400.measure_current

[Owning PyMeasure class, adapter and connection contract](overview.md)

measure_current(*nplc=1*, *current=0.000105*, *auto_range=True*)

Configure the measurement of current.

Parameters:

- **nplc** — NPLC power-line-cycle setting, from 0.01 to 10 (default: `1`)

- **current** — Upper current limit in Amps, from -1.05 A to 1.05 A (default: `0.000105`)

- **auto_range** — Turns on auto_range when True; otherwise uses the supplied current (default: `True`)

Deprecated since version 0.16: Current measurement setup now happens implicitly through `current`. Prefer - current nplc through `current_nplc`. - current range through `current_range` or `current_range_auto_enabled`.
