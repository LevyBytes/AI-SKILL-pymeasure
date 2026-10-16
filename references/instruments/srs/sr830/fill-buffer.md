# pymeasure.instruments.srs.SR830.fill_buffer

[Owning PyMeasure class, adapter and connection contract](overview.md)

fill_buffer(*count*, *has_aborted=<function SR830.&lt;lambda&gt;>*, *delay=0.001*)

Populate two numpy arrays from the instrument buffer contents.

Optionally wait until the requested number of recordings has completed.
