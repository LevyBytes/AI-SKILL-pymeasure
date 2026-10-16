# pymeasure.instruments.deltaelektronika.SM7045D.ramp_to_current

[Owning PyMeasure class, adapter and connection contract](overview.md)

ramp_to_current(*target_current*, *current_step=0.1*)

Ramp current upward or downward until it reaches the target current.

Parameters:

- **target_current** - Float defining the target current (in A)

- **current_step** - Optional float defining the current step size / ramp rate (in A/s) (default: `0.1`)
