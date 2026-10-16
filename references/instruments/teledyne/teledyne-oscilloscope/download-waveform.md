# pymeasure.instruments.teledyne.TeledyneOscilloscope.download_waveform

[Owning PyMeasure class, adapter and connection contract](overview.md)

download_waveform(*source*, *requested_points=None*, *sparsing=None*)

Read sampled data points from the selected oscilloscope source.

The call returns two np.ndarray objects for data and time values, plus a dict waveform preamble containing waveform metadata.

Parameters:

- **source** – measurement source; valid values are “C1”, “C2”, “C3”, “C4”, “MATH”.

- **requested_points** – count of points to acquire. If None, reuse the point count from the previous call, meaning the value currently stored in oscilloscope memory. If 0, return the largest available point count. (default: `None`)

- **sparsing** – spacing between returned data points. For example if sparsing = 4, one sample is read for every 4 stored points. If 0 or None, keep the sparsing from the prior call, namely the value recorded in oscilloscope memory. (default: `None`)

Returns:

data_ndarray, time_ndarray, waveform_preamble_dict: the waveform_preamble property describes the dict layout.
