# pymeasure.instruments.keithley.Keithley2000.wait_for_buffer

[Owning PyMeasure class, adapter and connection contract](overview.md)

wait_for_buffer(*should_stop=<function KeithleyBuffer.&lt;lambda&gt;>*, *timeout=60*, *interval=0.1*)

Block until the buffer becomes full. The call exits earlier when `should_stop` returns True or when timeout occurs first.

Parameters:

- **should_stop** — Function returning True when this call should exit before the buffer fills (default: `<function KeithleyBuffer.<lambda> at 0x7aa583874f60>`)

- **timeout** — Time in seconds after which this call exits early (default: `60`)

- **interval** — Time in seconds between checks for a full buffer (default: `0.1`)
