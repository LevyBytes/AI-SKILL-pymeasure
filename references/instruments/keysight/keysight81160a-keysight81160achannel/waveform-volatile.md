# pymeasure.instruments.keysight.keysight81160A.Keysight81160AChannel.waveform_volatile

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *waveform_volatile

Get volatile waveform data.

Warning: This property can differ from the current device volatile waveform. It returns only the waveform previously set via this driver. After a device power-cycle, external modification, or no prior waveform set, the returned value may be invalid or None.

Returns:

waveform data (array-like), or None when unset.
