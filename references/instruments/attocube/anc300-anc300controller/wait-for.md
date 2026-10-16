# pymeasure.instruments.attocube.anc300.ANC300Controller.wait_for

[Owning PyMeasure class, adapter and connection contract](overview.md)

wait_for(*query_delay=None*)

Pause briefly; `ask` uses this delay before it reads.

Parameters:

**query_delay** - Delay between writing and reading in seconds. None uses `query_delay`. (default: `None`)
