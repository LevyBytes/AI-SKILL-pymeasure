# pymeasure.instruments.keithley.Keithley6517B.ramp_to_voltage

[Owning PyMeasure class, adapter and connection contract](overview.md)

ramp_to_voltage(*target_voltage*, *steps=30*, *pause=0.02*)

Move from the currently set voltage to target voltage through a chosen number of linear steps, pausing between each step.

Parameters:

- **target_voltage**: Voltage value in Volts.

- **steps** - Integer step count. (default: `30`)

- **pause**: Pause duration in seconds between steps. (default: `0.02`)
