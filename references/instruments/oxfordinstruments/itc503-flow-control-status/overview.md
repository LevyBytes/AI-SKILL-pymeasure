# pymeasure.instruments.oxfordinstruments.ITC503.FLOW_CONTROL_STATUS

[Owning PyMeasure class, adapter and connection contract](../itc503/overview.md)

*class *FLOW_CONTROL_STATUS(**values*)

Bases: `IntFlag`

An IntFlag class used to interpret flow control status, with these flags:

| bit | flag | meaning |
| --- | --- | --- |
| 4 | HEATER_ERROR_SIGN | Heater-error sign indicator; True denotes negative |
| 3 | TEMPERATURE_ERROR_SIGN | Temperature-error sign indicator; True denotes negative |
| 2 | SLOW_VALVE_ACTION | Slow valve action occurring |
| 1 | COOLDOWN_TERMINATION | Cooldown-termination occurring |
| 0 | FAST_COOLDOWN | Fast-cooldown occurring |
