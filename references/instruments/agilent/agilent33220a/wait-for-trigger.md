# pymeasure.instruments.agilent.Agilent33220A.wait_for_trigger

[Owning PyMeasure class, adapter and connection contract](overview.md)

wait_for_trigger(*timeout=3600*, *should_stop=<function Agilent33220A.&lt;lambda&gt;>*)

Block until trigger activity completes or the timeout is reached.

Parameters:

- **timeout** – Upper bound for waiting. Crossing that limit raises TimeoutError. A zero timeout disables the timeout. (default: `3600`)

- **should_stop** – Optional callable returning a bool that can stop the wait before it completes. (default: `<function Agilent33220A.<lambda> at 0x7aa592a2e770>`)
