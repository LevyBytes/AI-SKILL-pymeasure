# pymeasure.instruments.siglenttechnologies.siglent_sds1000xhd.WaveformChannel.get_data

[Owning PyMeasure class, adapter and connection contract](overview.md)

get_data()

Return waveform data from the oscilloscope for the active source.

This method obtains waveform data from the oscilloscope and uses the preamble property for descriptor details about the waveform format.

Returns:

A (time_values, volt_values) tuple: - time_values: list of time samples in seconds - volt_values: list of voltage samples in volts

Return type:

tuple
