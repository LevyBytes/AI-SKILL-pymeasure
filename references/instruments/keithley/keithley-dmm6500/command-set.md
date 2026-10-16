# pymeasure.instruments.keithley.KeithleyDMM6500.command_set

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *command_set*: Any*

Select the command set used by the DMM6500. The instrument must be rebooted after this setting changes. Available values are `SCPI`, `TSP`, `SCPI2000`, and `SCPI34401`. The `KeithleyDMM6500` class is implemented for the `SCPI` command set only.

Note

For the TSP command set, send TSP commands directly with `write()` and `ask()` instead.
