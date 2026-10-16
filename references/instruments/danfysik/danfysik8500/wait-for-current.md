# pymeasure.instruments.danfysik.Danfysik8500.wait_for_current

[Owning PyMeasure class, adapter and connection contract](overview.md)

wait_for_current(*has_aborted=<function Danfysik8500.&lt;lambda&gt;>*, *delay=0.01*)

Wait until the current stabilizes. If supplied, `has_aborted` is called after each delay interval (in seconds) along with the stability check, allowing abort behavior to be integrated.

Parameters:

- **has_aborted** – Function returning True when waiting should stop (default: `<function Danfysik8500.<lambda> at 0x7aa5879e8510>`)

- **delay** – Seconds between stability checks (default: `0.01`)
