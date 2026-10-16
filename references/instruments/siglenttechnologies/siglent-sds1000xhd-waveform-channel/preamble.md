# pymeasure.instruments.siglenttechnologies.siglent_sds1000xhd.WaveformChannel.preamble

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *preamble

Return the waveform preamble descriptor data.

The preamble is binary metadata describing the waveform format. It includes offset and voltage scale, trigger delay, time interval, time division, ADC bit depth, probe attenuation factor, and voltage codes per division. Parsing follows the binary approach used by get_descriptor.

Returns:

A dictionary containing these keys:

- vdiv: Voltage per division (float)

- voffset: Voltage offset (float)

- interval: point-to-point time interval (float)

- trdl: Trigger delay (float)

- tdiv: Time per division (float)

- vcode_per: division-to-division voltage code factor (float)

- adc_bit: ADC bit depth (int)

- probe: Probe attenuation factor (float)

Return type:

dict
