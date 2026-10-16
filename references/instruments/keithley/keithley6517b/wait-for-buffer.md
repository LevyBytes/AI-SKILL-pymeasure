# pymeasure.instruments.keithley.Keithley6517B.wait_for_buffer

[Owning PyMeasure class, adapter and connection contract](overview.md)

wait_for_buffer(*should_stop=<function KeithleyBuffer.&lt;lambda&gt;>*, *timeout=60*, *interval=0.1*)

Block execution until the buffer is full. The call returns earlier if `should_stop` returns True or if timeout occurs before the buffer fills.

Parameters:

- **should_stop** — Function returning True when this call should exit early. (default: `<function KeithleyBuffer.<lambda> at 0x7aa583874f60>`)

- **timeout** — Time in seconds after which the call exits early. (default: `60`)

- **interval** — Time in seconds between buffer-full checks. (default: `0.1`)
