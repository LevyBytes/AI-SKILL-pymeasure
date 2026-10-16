# pymeasure.instruments.anaheimautomation.DPSeriesMotorController.move

[Owning PyMeasure class, adapter and connection contract](overview.md)

move(*direction*)

Move the stepper motor nonstop in the supplied direction until either a stop command is sent or a limit switch is reached. In the DP series instrument manuals, this is the 'slew' command.

Parameters:

**direction** - value assigned to the direction property before motor motion starts.
