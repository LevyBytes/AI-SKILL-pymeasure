# pymeasure.instruments.signalrecovery.DSP7265.buffer_to_float

[Owning PyMeasure class, adapter and connection contract](overview.md)

buffer_to_float(*buffer_data*, *sensitivity=None*, *sensitivity2=None*, *raise_error=True*)

Translate fixed-point buffer data into floating point data.

Conversion is attempted for as many provided fields as possible. To convert every supplied column, the input data must meet specific conditions; when a key cannot be converted, it is either left out of the returned data or causes an exception, controlled by raise_error.

The conversion conditions are:

- X, Y, magnitude, and noise conversion needs sensitivity data, supplied either inside the provided data or through the sensitivity argument.

- X2, Y2, and magnitude2 follow the same rule, using sensitivity2.

- Frequency conversion needs both ‘frequency part 1’ and ‘frequency part 2’.

Parameters:

- **buffer_data** (*dict*) – Input data for conversion. It must match the get_buffer return format: a dict containing numpy arrays.

- **sensitivity** – Optional sensitivity value for converting X, Y, magnitude, and noise. It may be a float or an array whose length matches the elements in buffer_data. When sensitivity is supplied and also exists in buffer_data, conversion uses the supplied value, while the buffer_data sensitivity is kept in the returned dict. (default: `None`)

- **sensitivity2** – Mirrors the first sensitivity argument, applied to X2, Y2, magnitude2, and noise2. (default: `None`)

- **raise_error** (*bool*) – Controls whether an exception is raised when any key in buffer_data cannot be converted. If False, unconvertible columns are excluded from the returned dict.

Returns:

Floating-point buffer data

Return type:

dict
