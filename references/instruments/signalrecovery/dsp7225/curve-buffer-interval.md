# pymeasure.instruments.signalrecovery.DSP7225.curve_buffer_interval

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *curve_buffer_interval*: Any*

Set the time interval between collection of successive curve-buffer points.

The time interval accepts integer ms values at 5 ms resolution; inputs are rounded up to a multiple of 5. Allowed values run from 0 to 1,000,000,000, corresponding to 12 days. Setting the interval to 0 changes data storage in the curve buffer to 1.25 ms/point (800 Hz). That mode only permits storage of the X and Y channel outputs. A CBD 3 command is unnecessary for this setup, because acquisition start performs it automatically.
