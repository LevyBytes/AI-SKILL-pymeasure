# pymeasure.instruments.keithley.Keithley2260B.applied

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *applied*: Any*

Set voltage (volts) and current (amps) together. Supply the pair as a tuple of (voltage, current). The actual output can diverge from the requested values according to whether the instrument is operating in constant current or constant voltage mode.
