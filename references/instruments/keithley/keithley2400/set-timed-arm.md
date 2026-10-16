# pymeasure.instruments.keithley.Keithley2400.set_timed_arm

[Owning PyMeasure class, adapter and connection contract](overview.md)

set_timed_arm(*interval*)

Configure measurement with the internal trigger at a variable sampling rate, where the interval in seconds separates sampling points.

Deprecated since version 0.16: Set `arm_source` to ?time? and use `arm_timer` to control the interval instead.
