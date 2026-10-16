# pymeasure.instruments.keithley.Keithley2200.wait_for

[Owning PyMeasure class, adapter and connection contract](overview.md)

wait_for(*query_delay=None*)

Pause for a period of time. `ask` uses this before reading.

Parameters:

**query_delay** (`Optional`[`float`]) – Seconds to wait between writing and reading. None uses the default delay. (default: `None`)

Return type:

`None`
