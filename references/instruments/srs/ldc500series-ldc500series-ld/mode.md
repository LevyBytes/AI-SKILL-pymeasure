# pymeasure.instruments.srs.ldc500series.LDC500SeriesLD.mode

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *mode*: Any*

Choose the laser diode control mode using str “CC” or “CP”.

When `mode` changes while the laser remains on, the controller uses a *bumpless transfer* for the live mode switch.

Changing `mode` from “CC” to “CP” samples the current photodiode current, equivalently optical power, then uses that measurement as the CP setpoint. If the measured photodiode current or power is over the setpoint limit, an error is raised.

Changing `mode` from “CP” to “CC” samples the current laser current and sets the CC setpoint to that measurement. Hardware prevents the measured laser current from exceeding the setpoint limit.
