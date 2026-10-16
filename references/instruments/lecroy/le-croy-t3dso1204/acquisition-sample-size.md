# pymeasure.instruments.lecroy.LeCroyT3DSO1204.acquisition_sample_size

[Owning PyMeasure class, adapter and connection contract](overview.md)

acquisition_sample_size(*source*)

Read the acquisition sample size for a selected channel, primarily for waveform capture. For source MATH, SANU? MATH appears not to respond correctly, so the memory size is returned instead.

Parameters:

**source** – Channel number or channel name.

Returns:

Returns the acquisition sample size for that channel.
