# pymeasure.instruments.thermotron.Thermotron3800.setpoint

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *setpoint*: Any*

Set the oven setpoint in Celsius. The float `setpoint` value is not applied until `run()` is invoked; after changing it, call `run()` so the oven moves to the requested temperature.

Returns:

None
