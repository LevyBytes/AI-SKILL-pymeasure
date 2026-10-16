# pymeasure.instruments.keithley.keithleyDMM6500.ScannerCard2000Channel.autorange_enabled

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *autorange_enabled*: Any*

Set the autorange state for the currently active mode.

Note
When the current active mode lacks autorange support, this command waits until the adapter's timeout and then raises -113 "Undefined header" error.
