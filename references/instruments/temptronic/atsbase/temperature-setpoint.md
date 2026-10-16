# pymeasure.instruments.temptronic.ATSBase.temperature_setpoint

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *temperature_setpoint*: Any*

Control selected setpoint’s temperature.

Type:

float

Valid range is -99.9 to 225.0 (?C), or the range specified by `temperature_limit_air_high` and `temperature_limit_air_low`. Use convenience function `set_temperature()` to avoid unexpected behavior.
