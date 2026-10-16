# pymeasure.instruments.signalrecovery.DSP7225.curve_buffer_status

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *curve_buffer_status*: Any*

Measure curve buffer acquisition status.

The command returns four values. **First value - Curve Acquisition Status:** This status number has 5 possibilities: state 0 means no activity; state 1 means acquisition via TD command is running; state 2 means acquisition by a TDC command is running; state 5 means acquisition via TD command is halted; state 6 means acquisition via TDC command is halted. **Second value - Number of Sweeps Acquired**: gives the sweeps already acquired. **Third value - Status Byte:** reports the status byte as a decimal value and matches the ST command response. **Fourth value - Number of Points Acquired:** gives the point count acquired in the curve buffer.
