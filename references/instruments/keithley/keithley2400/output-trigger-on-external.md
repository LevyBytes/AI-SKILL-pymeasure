# pymeasure.instruments.keithley.Keithley2400.output_trigger_on_external

[Owning PyMeasure class, adapter and connection contract](overview.md)

output_trigger_on_external(*line=1*, *after='DEL'*)

Configure output triggering on the selected trigger link line number, optionally choosing the measurement phase after which the trigger is generated (default to delay, immediately before measurement).

Parameters:

- **line** — Trigger line from 1 to 4 (default: `1`)

- **after** — Event string specifying trigger timing (default: `'DEL'`)

Deprecated since version 0.16: Use `trigger_output_event` and `trigger_output_line` instead.
