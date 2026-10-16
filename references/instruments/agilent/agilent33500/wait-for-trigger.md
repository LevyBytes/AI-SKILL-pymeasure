# pymeasure.instruments.agilent.Agilent33500.wait_for_trigger

[Owning PyMeasure class, adapter and connection contract](overview.md)

wait_for_trigger(*timeout=3600*, *should_stop=<function Agilent33500.&lt;lambda&gt;>*)

Block until triggering completes or until timeout is reached.

Parameters:

- **timeout** – Maximum duration allowed for the wait. A TimeoutError is raised if timeout is exceeded. When timeout is zero, waiting has no timeout. (default: `3600`)

- **should_stop** – Optional callable returning a bool that can end the wait early. (default: `<function Agilent33500.<lambda> at 0x7aa592a19010>`)
