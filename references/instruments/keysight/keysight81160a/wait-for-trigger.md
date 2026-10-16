# pymeasure.instruments.keysight.Keysight81160A.wait_for_trigger

[Owning PyMeasure class, adapter and connection contract](overview.md)

wait_for_trigger(*timeout=3600*, *should_stop=<function Agilent33500.&lt;lambda&gt;>*)

Block until triggering completes or the timeout is hit.

Parameters:

- **timeout** - Maximum permitted wait duration. Exceeding timeout raises TimeoutError. Setting timeout to zero disables the timeout. (default: `3600`)

- **should_stop** - Optional bool-returning function that can stop the wait before it finishes. (default: `<function Agilent33500.<lambda> at 0x7aa592a19010>`)
