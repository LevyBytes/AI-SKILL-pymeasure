# pymeasure.instruments.temptronic.ATSBase.temperature_setpoint_window

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *temperature_setpoint_window*: Any*

Control setpoint’s temperature window.

Type:

float

Valid range is between 0.1 to 9.9 (?C). The temperature status register flags `at temperature` once soak time has elapsed while temperature remains within this value?s bounds around the current setpoint.
