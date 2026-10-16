# pymeasure.instruments.keithley.Keithley2400Legacy.ramp_to_voltage

[Owning PyMeasure class, adapter and connection contract](overview.md)

ramp_to_voltage(*target_voltage*, *steps=30*, *pause=0.02*)

Move from the set voltage value to a target voltage across a chosen number of linear steps, with each step separated by a pause duration.

Parameters:

- **target_voltage** - voltage in Amps

- **steps** - integer number of steps (default: `30`)

- **pause** - pause duration in seconds between steps (default: `0.02`)
