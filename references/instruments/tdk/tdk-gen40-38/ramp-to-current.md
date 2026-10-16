# pymeasure.instruments.tdk.tdk_gen40_38.TDK_Gen40_38.ramp_to_current

[Owning PyMeasure class, adapter and connection contract](overview.md)

ramp_to_current(*target_current*, *steps=20*, *pause=0.2*)

Ramp from the set current value to a target current over a specified number of linear steps, with a pause duration between each step.

Parameters:

- **target_current** – Target current, in amps

- **steps** – Integer step count (default: `20`)

- **pause** – Seconds to wait between steps (default: `0.2`)
