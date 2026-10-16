# pymeasure.instruments.anaheimautomation.DPSeriesMotorController.absolute_position

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *absolute_position

Float property for the motor position value in absolute units. In DP series motor controller instrument manuals, 'absolute position' names the `step_position` property, not this property. This property also depends on subclass implementations of `steps_to_absolute()` and `absolute_to_steps()`. That lets the user choose how a motor step position maps into any desired absolute unit. For example, absolute units may be a linear stage position in meters, a gimbal mount angle, etc. This property is settable.
