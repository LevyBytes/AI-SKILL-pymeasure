# pymeasure.instruments.keithley.Keithley2260B.wait_for

[Owning PyMeasure class, adapter and connection contract](overview.md)

wait_for(*query_delay=None*)

Pause briefly. ‘ask’ uses this delay before a read.

Parameters:

**query_delay** (`Optional`[`float`]) – Time, in seconds, between the write and the following read. None selects the default delay. (default: `None`)

Return type:

`None`
