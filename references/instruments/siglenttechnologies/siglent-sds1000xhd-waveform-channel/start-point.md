# pymeasure.instruments.siglenttechnologies.siglent_sds1000xhd.WaveformChannel.start_point

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *start_point*: Any*

Set or read the first data point used for waveform transfer (int).

This command selects the first data point returned by :WAVeform:DATA?. Its range depends on the current waveform point and the value configured with :WAVeform:POINt. Use NR1 format (integer with no decimal point).
