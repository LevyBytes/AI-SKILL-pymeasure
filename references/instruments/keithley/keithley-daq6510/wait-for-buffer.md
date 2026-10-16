# pymeasure.instruments.keithley.KeithleyDAQ6510.wait_for_buffer

[Owning PyMeasure class, adapter and connection contract](overview.md)

wait_for_buffer(*should_stop=<function KeithleyBuffer.&lt;lambda&gt;>*, *timeout=60*, *interval=0.1*)

Block execution until the buffer is full. The function exits early if `should_stop` returns True, or if timeout is reached before a full buffer is available.

Parameters:

- **should_stop** – Function that returns True when this function should exit early (default: `<function KeithleyBuffer.<lambda> at 0x7aa583874f60>`)

- **timeout** – Time in seconds after which this function exits early (default: `60`)

- **interval** – Time in seconds between checks for whether the buffer is full (default: `0.1`)
