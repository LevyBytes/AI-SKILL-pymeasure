# pymeasure.instruments.kepco.KepcoBOP3612.current_setpoint

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *current_setpoint*: Any*

Control the output current setpoint.

Behavior changes with operating mode. In current mode, this programs the output current setpoint; achieved current is constrained by voltage compliance and load conditions (see: current). In voltage mode, it programs the compliance current for the related voltage set point. Queries return the programmed value, whose meaning depends on the power supply operating context (see: operating_mode).

The output still has to be enabled separately (see: output_enabled)
