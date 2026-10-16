# pymeasure.instruments.agilent.Agilent33220A.amplitude

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *amplitude*: Any*

Set the output waveform amplitude. The selected amplitude unit determines whether the value is Volt (peak-to-peak), Volt (RMS) or dBm. Limits vary with the configured output termination, with 50 Ohm to High Impedance changing by a factor of 2, and with the offset. The device may silently clip out-of-bound values (float, in V or dBm)
