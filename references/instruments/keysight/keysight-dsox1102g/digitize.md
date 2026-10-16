# pymeasure.instruments.keysight.KeysightDSOX1102G.digitize

[Owning PyMeasure class, adapter and connection contract](overview.md)

digitize(*source*)

Acquire waveforms using the settings configured by the :ACQuire commands. Keep a delay after digitize before issuing more commands, because timeout can occur before digitize finishes. :type source: `str` :param source: “channel1”, “channel2”, “function”, “math”, “fft”, “abus”, or “ext”.
