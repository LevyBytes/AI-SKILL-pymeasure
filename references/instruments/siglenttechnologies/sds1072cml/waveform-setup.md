# pymeasure.instruments.siglenttechnologies.SDS1072CML.waveform_setup

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *waveform_setup*: Any*

Choose how much waveform data is sent to the controller using a dict with these keys: - sparsing: interval between data points (0 and 1 return all points, 4 returns 1 out of 4 points, etc…) - number: maximum data points to return. 0 returns all points - first: index of the first data point for transfer (0 is first)
