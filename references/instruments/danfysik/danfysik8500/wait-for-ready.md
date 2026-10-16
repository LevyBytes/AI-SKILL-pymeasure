# pymeasure.instruments.danfysik.Danfysik8500.wait_for_ready

[Owning PyMeasure class, adapter and connection contract](overview.md)

wait_for_ready(*has_aborted=<function Danfysik8500.&lt;lambda&gt;>*, *delay=0.01*)

Wait until the instrument is ready. If supplied, `has_aborted` is called after each delay interval (in seconds) along with the readiness check, allowing abort behavior to be integrated.

Parameters:

- **has_aborted** – Function returning True when waiting should stop (default: `<function Danfysik8500.<lambda> at 0x7aa5879e87d0>`)

- **delay** – Seconds between readiness checks (default: `0.01`)
