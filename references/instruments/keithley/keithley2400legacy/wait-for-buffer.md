# pymeasure.instruments.keithley.Keithley2400Legacy.wait_for_buffer

[Owning PyMeasure class, adapter and connection contract](overview.md)

wait_for_buffer(*should_stop=<function KeithleyBuffer.&lt;lambda&gt;>*, *timeout=60*, *interval=0.1*)

Block program execution until the buffer is full. This function returns early if `should_stop` returns True, or when timeout is reached before the buffer fills.

Parameters:

- **should_stop** - function returning True when this function should return early (default: `<function KeithleyBuffer.<lambda> at 0x7aa583874f60>`)

- **timeout** - time in seconds after which this function should return early (default: `60`)

- **interval** - seconds between checks of whether the buffer is full (default: `0.1`)
