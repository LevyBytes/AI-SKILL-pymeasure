# pymeasure.instruments.anaheimautomation.DPSeriesMotorController.step_position

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *step_position

Integer property for motor position in steps. Steps are counted by the motor controller, or by an externally connected encoder when `encoder_enabled` is set. In DP series motor controller instrument manuals, this property is called the 'absolute position'; this driver instead converts between steps and absolute units through the `absolute_position` property. This property can be set.
