# pymeasure.instruments.keithley.KeithleyDMM6500.nplc

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *nplc*: Any*

Set integration time for the currently active `mode` in number of power line cycles (NPLC). It controls measurement duration for the input signal. Use 0.0005 to 15 at 60Hz, or 12 at 50Hz or 400Hz.

Note

`voltage`, `current`, `resistance`, `resistance 4W`, `diode`, `temperature`, and `voltage ratio` mode are the only modes with NPLC support. If the active mode lacks NPLC, the command waits for the adapter timeout and then raises -113 "Undefined header".
