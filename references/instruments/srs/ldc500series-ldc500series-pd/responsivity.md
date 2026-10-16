# pymeasure.instruments.srs.ldc500series.LDC500SeriesPD.responsivity

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *responsivity*: Any*

Set or read photodiode responsivity as a float in uA/mW.

Changing `responsivity`, whether directly or through `calibrate`, also updates:

- `current_setpoint` and `current_limit` when `units == "mW"`

- `power_setpoint` and `power_limit` when `units == "uA"`

Those updates preserve these relationships:

- `current_setpoint = power_setpoint x responsivity`

- `current_limit = power_limit x responsivity`
