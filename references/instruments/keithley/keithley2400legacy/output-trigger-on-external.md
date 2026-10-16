# pymeasure.instruments.keithley.Keithley2400Legacy.output_trigger_on_external

[Owning PyMeasure class, adapter and connection contract](overview.md)

output_trigger_on_external(*line=1*, *after='DEL'*)

Configure output triggering on the selected trigger link line number. Optionally choose the part of the measurement after which the trigger is generated; default is delay, immediately before the measurement.

Parameters:

- **line** - trigger line from 1 to 4 (default: `1`)

- **after** - event string determining when to trigger (default: `'DEL'`)
