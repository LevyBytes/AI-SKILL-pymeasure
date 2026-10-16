# pymeasure.instruments.teledyne.teledyne_oscilloscope.TeledyneOscilloscopeChannel.trigger_coupling

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *trigger_coupling*: Any*

Set input coupling for the selected trigger sources using a string.

- ac: AC coupling blocks the DC component in the trigger path, which removes dc offset voltage from the trigger waveform. Use AC coupling for a stable edge trigger when the waveform carries a large dc offset.

- dc: DC coupling passes both dc and ac signals into the trigger path.

- lowpass: HFREJ coupling inserts a lowpass filter into the trigger path.

- highpass: LFREJ coupling inserts a highpass filter into the trigger path.
