# pymeasure.instruments.spellmanhv.spellmanXRV.UnscaledData.analog_monitor

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *analog_monitor*: Any*

Read the analog monitor feedback values.

Returns:

dict of int from `0` to `4095`

Dict keys:

`voltage`, `current`, `filament`, `voltage_setpoint`, `current_setpoint`, `limit`, `preheat`, `anode_current`

`voltage_setpoint`, `current_setpoint`, `limit`, and `preheat` apply only during local mode operation.

`anode_current` applies only to bipolar units.
