# pymeasure.instruments.yokogawa.YokogawaGS200.trigger_ramp_to_level

[Owning PyMeasure class, adapter and connection contract](overview.md)

trigger_ramp_to_level(*level*, *ramp_time*)

Start a ramp from the current output level to “level” over “ramp_time”. This method does NOT wait for the ramp to finish, so later code evaluation is not blocked.

Parameters:

- **level** (*float*) – final output level

- **ramp_time** (*float*) – ramp duration in seconds

Returns:

None
