# pymeasure.instruments.keithley.Keithley2450.ramp_to_current

[Owning PyMeasure class, adapter and connection contract](overview.md)

ramp_to_current(*target_current*, *steps=30*, *pause=0.02*)

Move from the configured current value to a target current in a specified count of linear steps, pausing between each step.

Parameters:

- **target_current** - Current in Amps

- **steps** - Integer step count (default: `30`)

- **pause** - Pause duration in seconds between steps (default: `0.02`)
