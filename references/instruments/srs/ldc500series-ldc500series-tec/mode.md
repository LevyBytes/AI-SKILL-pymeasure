# pymeasure.instruments.srs.ldc500series.LDC500SeriesTEC.mode

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *mode*: Any*

Set/read TEC control mode using str “CC” or “CT”.

If `mode` changes while the TEC is on, the controller uses a *bumpless transfer* for a live control-mode switch.

Changing `mode` from “CT” to “CC” samples the present TEC current and applies that measurement as the CC setpoint.

Changing `mode` from “CC” to “CT” samples the present temperature sensor value and applies that measurement as the CT setpoint.
