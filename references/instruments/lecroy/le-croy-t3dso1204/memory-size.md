# pymeasure.instruments.lecroy.LeCroyT3DSO1204.memory_size

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *memory_size*: Any*

Set the maximum memory depth.

&lt;size&gt;:={7K,70K,700K,7M} in non-interleaved mode, where one active channel uses each A/D converter. Most oscilloscopes provide two channels per A/D converter.

&lt;size&gt;:={14K,140K,1.4M,14M} in interleave mode, where more than one channel is active on an A/D converter.
