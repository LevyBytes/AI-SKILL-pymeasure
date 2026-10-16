# pymeasure.instruments.keysight.Keysight33250A.wait_for_trigger

[Owning PyMeasure class, adapter and connection contract](overview.md)

wait_for_trigger(*timeout=None*, *should_stop=<function Keysight33250A.&lt;lambda&gt;>*)

Block until triggering is complete.

This method sends `*OPC?`, then waits for the instrument response `"1"`.

Parameters:

- **timeout** (`Optional`[`float`]) – Upper wait duration in seconds. `None` means wait without a time limit. (default: `None`)

- **should_stop** (`Callable`[[], `bool`]) – Callback that returns `True` to stop waiting before completion. (default: `<function Keysight33250A.<lambda> at 0x7aa581663cc0>`)

Raises:

**TimeoutError** – Raised when `timeout` is not `None` and completion does not occur before expiration.

Return type:

`None`
