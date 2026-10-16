# pymeasure.instruments.siglenttechnologies.siglent_sds1000xhd.WaveformChannel.max_point

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *max_point*: Any*

Return the per-piece maximum point count used when waveform data is read in pieces (float).

This query reports how many points one piece can contain when waveform data must be split into pieces. Use it to plan segmented transfers for large waveforms.
