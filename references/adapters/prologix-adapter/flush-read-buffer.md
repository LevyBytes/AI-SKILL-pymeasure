# pymeasure.adapters.PrologixAdapter.flush_read_buffer

[Owning PyMeasure class, adapter and connection contract](overview.md)

flush_read_buffer()

Clear and drop the input buffer.

Following pyvisa behavior, the read and receive buffers are discarded. If the read buffer contained data without an END-indicator, the device is read until an END indicator appears, which drops that data.

Return type:

`None`
