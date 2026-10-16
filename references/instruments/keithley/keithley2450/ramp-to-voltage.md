# pymeasure.instruments.keithley.Keithley2450.ramp_to_voltage

[Owning PyMeasure class, adapter and connection contract](overview.md)

ramp_to_voltage(*target_voltage*, *steps=30*, *pause=0.02*)

Move from the configured voltage value to a target voltage in a specified count of linear steps, pausing between each step.

Parameters:

- **target_voltage** - Voltage in Amps

- **steps** - Integer step count (default: `30`)

- **pause** - Pause duration in seconds between steps (default: `0.02`)
