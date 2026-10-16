# pymeasure.instruments.signalrecovery.DSP7225.curve_buffer_length

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *curve_buffer_length*: Any*

Set the curve buffer length.

Allowed values are integers from 1 through 32,768, but the actual maximum point count depends on how many curves are stored, as configured by the curve_buffer_bits property (32,768 / n).
