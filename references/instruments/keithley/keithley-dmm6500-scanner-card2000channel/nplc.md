# pymeasure.instruments.keithley.keithleyDMM6500.ScannerCard2000Channel.nplc

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *nplc*: Any*

Set integration time as a count of power line cycles (NPLC). Valid values are 0.0005 to 15 for 60Hz, with 12 as the upper value for 50Hz or 400Hz. This command applies only to `voltage`, 2-wire ohms, and 4-wire ohms.

Note

NPLC setting is supported only in these modes: `voltage`, `current`, `resistance`, `resistance 4W`, `diode`, `temperature`, and `voltage ratio`. When the current active mode lacks NPLC support, this command waits until the adapter's timeout and then raises -113 "Undefined header" error.
