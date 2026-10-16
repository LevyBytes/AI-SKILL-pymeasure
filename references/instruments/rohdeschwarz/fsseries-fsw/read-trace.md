# pymeasure.instruments.rohdeschwarz.fsseries.FSW.read_trace

[Owning PyMeasure class, adapter and connection contract](overview.md)

read_trace(*n_trace=1*)

Read data from the active trace.

Parameters:

**n_trace** – Trace selector, numbered 1-6; the default is 1. (default: `1`)

Returns:

Trace data as a 2d numpy array, [[frequency], [amplitude]].
