# pymeasure.instruments.anaheimautomation.DPSeriesMotorController.home

[Owning PyMeasure class, adapter and connection contract](overview.md)

home(*home_mode*)

Send the motor controller the command that homes the motor.

Parameters:

**home_mode** –

`0` or `1`, choosing the homing mode to run.

Mode 0 runs homing by moving the motor until it reaches a soft limit; the controller then ramps down to base speed and keeps moving until it reaches a home limit.

In mode 1, the controller moves the motor until it reaches a limit, then ramps down to base speed, reverses direction, and runs until that limit is released.
