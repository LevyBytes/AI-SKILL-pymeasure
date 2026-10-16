# pymeasure.instruments.signalrecovery.DSP7225.get_buffer

[Owning PyMeasure class, adapter and connection contract](overview.md)

get_buffer(*quantity=None*, *convert_to_float=True*, *wait_for_buffer=True*)

Retrieve the buffer after filling completes. Data read from the lock-in uses fixed-point format and must be translated before it can be understood as meaningful data. When convert_to_float is True, conversion is performed before the data is returned, if possible.

Parameters:

- **quantity** (*str*) – Optional name of the quantity to retrieve from the curve buffer. Valid choices include ‘x’, ‘y’, ‘magnitude’, and ‘phase’; also ‘sensitivity’, ‘adc1’, ‘adc2’, ‘adc3’, ‘dac1’, and ‘dac2’; plus ‘noise’, ‘ratio’, ‘log ratio’, ‘event’, ‘frequency part 1’, and ‘frequency part 2’. In both dual modes, the extra choices are ‘x2’, ‘y2’, ‘magnitude2’, ‘phase2’, and ‘sensitivity2’. If quantity is not provided, every available data item is retrieved.

- **convert_to_float** (*bool*) – Bool selecting whether fixed-point buffer-data is converted through the buffer_to_float method into meaningful floating point values. If True, this method attempts to convert all available data into meaningful values; failure to do so raises an exception. If False, conversion is skipped and raw buffer-data is returned.

- **wait_for_buffer** (*bool*) – Bool selecting whether to wait for data acquisition to finish when this method is called before completion. If True, execution waits until the buffer is filled. If False, an exception is raised if acquisition has not finished at call time.
