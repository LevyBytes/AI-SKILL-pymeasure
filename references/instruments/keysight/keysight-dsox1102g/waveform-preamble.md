# pymeasure.instruments.keysight.KeysightDSOX1102G.waveform_preamble

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *waveform_preamble

Return preamble information for the selected waveform source as a dict. Keys include “format” for byte, word, or ascii (str); “type” for normal, peak detect, or average (str); “points” for nb of data points transferred (int); “count”, which is always 1 (int); “xincrement” for time between data points (float); “xorigin” for first memory data point (float); “xreference” for the data point associated with xorigin (int); “yincrement” for voltage between data points (float); “yorigin” for voltage at screen center (float); and “yreference” for the data point associated with yorigin (int).
