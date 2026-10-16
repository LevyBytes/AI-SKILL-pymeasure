# pymeasure.instruments.Channel.wait_for

[Owning PyMeasure class, adapter and connection contract](overview.md)

wait_for(*query_delay=None*)

Pause for a specified time; ‘ask’ uses this interval before reading.

Parameters:

**query_delay** (`Optional`[`float`]) – Seconds to pause after writing before reading. `None` uses the default delay. (default: `None`)

Return type:

`None`
