# pymeasure.instruments.signalrecovery.DSP7225.set_buffer

[Owning PyMeasure class, adapter and connection contract](overview.md)

set_buffer(*points*, *quantities=None*, *interval=0.01*)

Prepare the curve buffer before measurement.

Parameters:

- **points** (*int*) – Number of points to record in the curve buffer

- **quantities** (*list*) – List of quantity strings to record in the curve buffer. Options include ‘x’, ‘y’, ‘magnitude’, and ‘phase’; ‘sensitivity’, ‘adc1’, ‘adc2’, ‘adc3’, ‘dac1’, and ‘dac2’; ‘noise’, ‘ratio’, ‘log ratio’, ‘event’, and ‘frequency’ (or ‘frequency part 1’ and ‘frequency part 2’). In both dual modes, additional options are ‘x2’, ‘y2’, ‘magnitude2’, ‘phase2’, and ‘sensitivity2’. Default is ‘x’ and ‘y’.

- **interval** (*float*) – Interval in s between two subsequent points stored in the curve buffer. Default is 10 ms.
