# pymeasure.instruments.signalrecovery.DSP7225.buffer_to_float

[Owning PyMeasure class, adapter and connection contract](overview.md)

buffer_to_float(*buffer_data*, *sensitivity=None*, *sensitivity2=None*, *raise_error=True*)

Translate fixed-point buffer data into floating point data.

Conversion is attempted for as much of the supplied data as possible, but converting all supplied columns depends on data requirements; any key that cannot be converted is either left out of the returned data or triggers an exception, according to raise_error.

These are the requirements for data conversion:

- To convert X, Y, magnitude and noise, sensitivity data is required; that data may be included in the supplied data or passed with the sensitivity argument.

- The same rule applies to X2, Y2 and magnitude2 when using sensitivity2.

- Frequency conversion needs both ‘frequency part 1’ and ‘frequency part 2’.

Parameters:

- **buffer_data** (*dict*) – Data slated for conversion. It must use the format returned by the get_buffer method: a dict of numpy arrays.

- **sensitivity** – Optional sensitivity value used when converting X, Y, magnitude and noise. It may be a float, or an array whose length matches elements in buffer_data. When sensitivity is supplied and buffer_data also contains sensitivity, conversion uses the supplied value, while the sensitivity from buffer_data is kept in the returned dict. (default: `None`)

- **sensitivity2** – Equivalent to the first sensitivity argument, except it applies to X2, Y2, magnitude2 and noise2. (default: `None`)

- **raise_error** (*bool*) – Controls whether an exception is raised when some keys in buffer_data cannot be converted. If False, unconvertible columns are left out of the returned dict.

Returns:

Floating-point buffer data

Return type:

dict
