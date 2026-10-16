# pymeasure.instruments.keithley.Keithley2400.ramp_to_current

[Owning PyMeasure class, adapter and connection contract](overview.md)

ramp_to_current(*target_current*, *steps=30*, *pause=0.02*)

Move from the set current value to the target current in linear steps, waiting the pause duration between steps.

Parameters:

- **target_current** — Current value in Amps

- **steps** — Integer count of steps (default: `30`)

- **pause** — Pause duration in seconds between steps (default: `0.02`)
