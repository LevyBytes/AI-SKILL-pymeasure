# pymeasure.instruments.keithley.Keithley2400.ramp_to_voltage

[Owning PyMeasure class, adapter and connection contract](overview.md)

ramp_to_voltage(*target_voltage*, *steps=30*, *pause=0.02*)

Move from the present voltage value to the target voltage in linear steps, waiting the pause duration between steps.

Parameters:

- **target_voltage** — Voltage value in Amps

- **steps** — Integer count of steps (default: `30`)

- **pause** — Pause duration in seconds between steps (default: `0.02`)
