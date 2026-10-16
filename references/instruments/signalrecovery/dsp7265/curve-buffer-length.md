# pymeasure.instruments.signalrecovery.DSP7265.curve_buffer_length

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *curve_buffer_length*: Any*

Set the curve buffer length.

Accepted values are integers from 1 through 32,768. The effective maximum number of points depends on how many curves are stored, configured by the curve_buffer_bits property (32,768 / n).
