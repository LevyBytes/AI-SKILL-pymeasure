# pymeasure.instruments.keithley.Keithley2400Legacy.ramp_to_current

[Owning PyMeasure class, adapter and connection contract](overview.md)

ramp_to_current(*target_current*, *steps=30*, *pause=0.02*)

Move from the set current value to a target current across a chosen number of linear steps, with each step separated by a pause duration.

Parameters:

- **target_current** - current in Amps

- **steps** - integer number of steps (default: `30`)

- **pause** - pause duration in seconds between steps (default: `0.02`)
