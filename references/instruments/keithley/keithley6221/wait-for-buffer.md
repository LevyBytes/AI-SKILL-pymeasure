# pymeasure.instruments.keithley.Keithley6221.wait_for_buffer

[Owning PyMeasure class, adapter and connection contract](overview.md)

wait_for_buffer(*should_stop=<function KeithleyBuffer.&lt;lambda&gt;>*, *timeout=60*, *interval=0.1*)

Block execution until the buffer is full. This function returns early when `should_stop` returns True or when timeout arrives before the buffer fills.

Parameters:

- **should_stop** – Predicate checked for early exit; return True to make this function return early (default: `<function KeithleyBuffer.<lambda> at 0x7aa583874f60>`)

- **timeout** – Time in seconds after which this function should return early (default: `60`)

- **interval** – Time in seconds between checks for whether the buffer is full (default: `0.1`)
