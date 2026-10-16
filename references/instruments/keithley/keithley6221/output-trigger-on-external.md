# pymeasure.instruments.keithley.Keithley6221.output_trigger_on_external

[Owning PyMeasure class, adapter and connection contract](overview.md)

output_trigger_on_external(*line=1*, *after='DEL'*)

Configure output triggering for a chosen trigger link line number, optionally naming the measurement phase after which the trigger is produced (default to delay, which is just before measurement)

Parameters:

- **line** – Trigger line from 1 to 4 (default: `1`)

- **after** – Event string selecting when to trigger (default: `'DEL'`)
