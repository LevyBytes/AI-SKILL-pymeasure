# pymeasure.instruments.temptronic.ATSBase.temperature_soak_time

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *temperature_soak_time*: Any*

Set the soak time for the currently selected setpoint.

Type:

float

Valid range is between 0 to 9999 (s). Lower values reduce cycle times; higher values lengthen cycles but can reduce settling errors. See `temperature_setpoint_window` for details.
