# pymeasure.instruments.keysight.keysight81160A.Keysight81160AChannel.save_waveform

[Owning PyMeasure class, adapter and connection contract](overview.md)

save_waveform(*waveform*, *name*)

Store a waveform in the generator's nonvolatile memory.

Parameters:

- **waveform** – The waveform data.

- **name** - Waveform memory identifier. It can contain up to 12 characters; the first one must be a letter (A-Z), and later characters may be numbers (0-9) or the underscore character ('_'). Blank spaces are not allowed.
