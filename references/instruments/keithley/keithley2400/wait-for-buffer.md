# pymeasure.instruments.keithley.Keithley2400.wait_for_buffer

[Owning PyMeasure class, adapter and connection contract](overview.md)

wait_for_buffer(*should_stop=<function KeithleyBuffer.&lt;lambda&gt;>*, *timeout=60*, *interval=0.1*)

Block until the buffer is full. The call returns sooner if `should_stop` returns True or if `timeout` expires first.

Parameters:

- **should_stop** — Early-exit callback; returning True ends the wait before the buffer is full (default: `<function KeithleyBuffer.<lambda> at 0x7aa583874f60>`)

- **timeout** — Time in seconds after which this function returns early (default: `60`)

- **interval** — Time in seconds between buffer-full checks (default: `0.1`)
