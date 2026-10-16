# pymeasure.instruments.signalrecovery.DSP7265.curve_buffer_interval

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *curve_buffer_interval*: Any*

Set the time spacing used when successive points are collected into the curve buffer.

The time interval accepts integer ms values at 5 ms resolution; inputs are rounded upward to a multiple of 5. Values may range from 0 through 1,000,000,000, which corresponds to 12 days. Setting the interval to 0 makes curve-buffer storage run at 1.25 ms/point (800 Hz), but only X and Y channel outputs can be stored. No CBD 3 command is needed for this setup because acquisition start performs it automatically.
