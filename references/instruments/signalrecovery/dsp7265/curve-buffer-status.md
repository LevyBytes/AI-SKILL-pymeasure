# pymeasure.instruments.signalrecovery.DSP7265.curve_buffer_status

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *curve_buffer_status*: Any*

Read the acquisition status for the curve buffer.

Four values come back: **First value - Curve Acquisition Status:** one of 5 status codes, where 0 means no activity, 1 means acquisition via TD command running, 2 means acquisition by a TDC command running, 5 means acquisition via TD command halted, and 6 means acquisition bia TDC command halted. **Second value - Number of Sweeps Acquired**: sweeps already acquired. **Third value - Status Byte:** decimal form of the status byte; ST returns the same response. **Fourth value - Number of Points Acquired:** points in the curve buffer that have been acquired.
