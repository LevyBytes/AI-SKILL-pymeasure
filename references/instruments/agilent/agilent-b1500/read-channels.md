# pymeasure.instruments.agilent.agilentB1500.AgilentB1500.read_channels

[Owning PyMeasure class, adapter and connection contract](overview.md)

read_channels(*nchannels*)

Read one measurement point from the buffer for the requested channel count.

Parameters:

**nchannels** (*int*) – Count of channels returning data, including measurement channels and sweep sources according to data output settings

Returns:

Measurement data

Return type:

tuple
