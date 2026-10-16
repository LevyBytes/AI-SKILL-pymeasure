# pymeasure.instruments.keithley.KeithleyDMM6500.autorange_enabled

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *autorange_enabled*: Any*

Set the autorange state for the currently active `mode`.

Note

When the active mode has no autorange command, this call waits for the adapter timeout and then reports -113 "Undefined header".
