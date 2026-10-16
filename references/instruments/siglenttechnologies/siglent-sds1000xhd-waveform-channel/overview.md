# pymeasure.instruments.siglenttechnologies.siglent_sds1000xhd.WaveformChannel

*class *pymeasure.instruments.siglenttechnologies.siglent_sds1000xhd.WaveformChannel(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

SDS1000XHD oscilloscope waveform channel.

Use this class to read waveform data from the oscilloscope. A waveform record has two parts: the preamble and the waveform data. The preamble supplies the metadata needed to decode the sample data; the waveform data contains the acquired values for each point in the selected source. Read each part with its own command.
