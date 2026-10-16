# pymeasure.instruments.kepco.KepcoBOP3612.voltage_setpoint

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *voltage_setpoint*: Any*

Control the output voltage setpoint.

Behavior changes with operating mode. In voltage mode, this programs the output voltage setpoint; achieved voltage is constrained by current compliance and load conditions (see: voltage). In current mode, it programs the compliance voltage for the related current set point. Queries return the programmed value, whose meaning depends on the power supply operating context (see: operating_mode).

The output still has to be enabled separately (see: output_enabled)
