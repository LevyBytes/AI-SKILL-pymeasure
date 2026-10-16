# pymeasure.adapters.ProtocolAdapter.flush_read_buffer

[Owning PyMeasure class, adapter and connection contract](overview.md)

flush_read_buffer()

Clear the input buffer by flushing and discarding it.

Following pyvisa behavior, the read buffer contents are discarded; when the read buffer held data without an END-indicator, the device is read until an END indicator is encountered, losing data in the process.

Return type:

`None`
