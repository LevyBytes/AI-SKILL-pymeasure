# pymeasure.instruments.keysight.KeysightDSOX1102G.download_data

[Owning PyMeasure class, adapter and connection contract](overview.md)

download_data(*source*, *points=62500*)

Return oscilloscope data for the selected source. The result contains a np.ndarray of data values without a temporal axis, plus a dict waveform preamble that can be used to construct the matching time values for each data point.

For a valid acquisition, the multimeter is stopped.

Parameters:

- **source** – measurement source; allowed values are “channel1”, “channel2”, “function”, “fft”, “wmemory1”, “wmemory2”, or “ext”.

- **points** – integer count of points to acquire. The oscilloscope can return fewer points than requested; that behavior is not a library problem. Valid values are 100, 250, 500, and 1000; larger choices are 2000, 5000, 10000, 20000, 50000, or 62500. (default: `62500`)

Return data_ndarray, waveform_preamble_dict:

For the dict layout, see the waveform_preamble property.
