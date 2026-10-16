# pymeasure.instruments.oxfordinstruments.IPS120_10.wait_for_idle

[Owning PyMeasure class, adapter and connection contract](overview.md)

wait_for_idle(*delay=1*, *max_wait_time=None*, *should_stop=<function IPS120_10.&lt;lambda&gt;>*)

Blocks until the system is idle, meaning the current or field is not ramping.

Parameters:

- **delay** - Seconds between successive state queries to the instrument. (default: `1`)

- **max_wait_time** - Maximum number of seconds to wait for the system to become at rest. If it is still not at rest after this time, `TimeoutError` is raised. `None` means there is no maximum time. (default: `None`)

- **should_stop** - Function returning `True` when `wait_for_idle` should return before normal completion. (default: `<function IPS120_10.<lambda> at 0x7aa57f5de140>`)
