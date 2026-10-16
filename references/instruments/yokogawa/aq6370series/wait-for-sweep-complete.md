# pymeasure.instruments.yokogawa.aq6370series.AQ6370Series.wait_for_sweep_complete

[Owning PyMeasure class, adapter and connection contract](overview.md)

wait_for_sweep_complete(*should_stop=<function AQ6370Series.&lt;lambda&gt;>*, *timeout=3600*, *delay=0*)

Block program execution while waiting until the sweep completes.

Parameters:

- **should_stop** – Function returning True when waiting should stop. (default: `<function AQ6370Series.<lambda> at 0x7aa57c817270>`)

- **timeout** – Maximum wait time in seconds. (default: `3600`)

- **delay** – Seconds to pause between sweep-completion checks. (default: `0`)

Returns:

True means the sweep completed; False means should_stop ended the wait.

Raises:

**TimeoutError** – Raised when the sweep is not complete before the timeout period ends.
