# pymeasure.instruments.common_base.CommonBase.wait_for

[Owning PyMeasure class, adapter and connection contract](overview.md)

wait_for(*query_delay=None*)

Pause for a period of time. `ask` uses this wait before reading.

Implement in subclass!

Parameters:

**query_delay** (`Optional`[`float`]) - Seconds to wait between writing and reading. None selects the default delay. (default: `None`)

Return type:

`None`
