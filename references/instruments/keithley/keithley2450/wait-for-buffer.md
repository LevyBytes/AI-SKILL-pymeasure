# pymeasure.instruments.keithley.Keithley2450.wait_for_buffer

[Owning PyMeasure class, adapter and connection contract](overview.md)

wait_for_buffer(*should_stop=<function KeithleyBuffer.&lt;lambda&gt;>*, *timeout=60*, *interval=0.1*)

Block program execution until the buffer is full. The function returns before that if `should_stop` returns True or if timeout is reached first.

Parameters:

- **should_stop** - Function whose True result makes this function return early (default: `<function KeithleyBuffer.<lambda> at 0x7aa583874f60>`)

- **timeout** - Time in seconds after which this function should return early (default: `60`)

- **interval** - Time in seconds between checks for a full buffer (default: `0.1`)
