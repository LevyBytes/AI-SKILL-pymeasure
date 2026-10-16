# pymeasure.instruments.lecroy.LeCroyT3DSO1204.download_waveform

[Owning PyMeasure class, adapter and connection contract](overview.md)

download_waveform(*source*, *requested_points=None*, *sparsing=None*)

Read data points from the chosen oscilloscope source.

The call returns two np.ndarray objects, one for data points and one for time points, plus a dict containing the waveform preamble metadata.

Parameters:

- **source** – Measurement source; valid choices are “C1”, “C2”, “C3”, “C4”, and “MATH”.

- **requested_points** – Number of points to acquire. If None, the request reuses the point count from the previous call, namely the number of points stored in oscilloscope memory. If 0, the maximum point count is returned. (default: `None`)

- **sparsing** – Interval between data points. For example, if sparsing = 4, the read keeps one point out of every 4. If 0 or None, the previous call’s sparsing is reused, which is the sparsing value stored in oscilloscope memory. (default: `None`)

Returns:

data_ndarray, time_ndarray, waveform_preamble_dict: dict layout is described by the waveform_preamble property.
