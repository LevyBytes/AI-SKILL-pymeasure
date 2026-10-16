# pymeasure.instruments.signalrecovery.DSP7265.get_buffer

[Owning PyMeasure class, adapter and connection contract](overview.md)

get_buffer(*quantity=None*, *convert_to_float=True*, *wait_for_buffer=True*)

Fetch the buffer once filling is complete. Data read from the lock-in uses fixed-point format, so it must be translated before it represents meaningful data. If convert_to_float is True, conversion runs before data is returned when conversion is possible.

Parameters:

- **quantity** (*str*) – Optional name of the curve-buffer quantity to retrieve. Single-channel choices are ‘x’ and ‘y’; vector choices are ‘magnitude’ and ‘phase’; input choices are ‘sensitivity’, ‘adc1’, ‘adc2’, and ‘adc3’; output choices are ‘dac1’ and ‘dac2’; other choices are ‘noise’, ‘ratio’, ‘log ratio’, ‘event’, ‘frequency part 1’, and ‘frequency part 2’. In both dual modes, the additional choices are ‘x2’, ‘y2’, ‘magnitude2’, ‘phase2’, and ‘sensitivity2’. When quantity is not provided, all available data is retrieved.

- **convert_to_float** (*bool*) – Boolean switch for converting fixed-point buffer-data into meaningful floating point values through buffer_to_float. If True, the method attempts conversion for every available data field and raises an exception when that cannot be done. If False, conversion is skipped and raw buffer-data is returned.

- **wait_for_buffer** (*bool*) – Boolean switch for waiting when this method is called before data acquisition has finished. If True, execution waits until the buffer is full before proceeding. If False, an exception is raised when acquisition is still incomplete at call time.
