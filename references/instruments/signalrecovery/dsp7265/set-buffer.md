# pymeasure.instruments.signalrecovery.DSP7265.set_buffer

[Owning PyMeasure class, adapter and connection contract](overview.md)

set_buffer(*points*, *quantities=None*, *interval=0.01*)

Ready the curve buffer for a measurement.

Parameters:

- **points** (*int*) – Number of points that will be recorded in the curve buffer

- **quantities** (*list*) – List of string quantities to record in the curve buffer. Choices include ‘x’ and ‘y’; ‘magnitude’ and ‘phase’; ‘sensitivity’, ‘adc1’, ‘adc2’, and ‘adc3’; ‘dac1’ and ‘dac2’; ‘noise’, ‘ratio’, ‘log ratio’, and ‘event’; plus ‘frequency’ (or ‘frequency part 1’ and ‘frequency part 2’). In both dual modes, additional choices are ‘x2’, ‘y2’, ‘magnitude2’, ‘phase2’, and ‘sensitivity2’. Default is ‘x’ and ‘y’.

- **interval** (*float*) – Time, in s, separating consecutive curve-buffer points. Default is 10 ms.
