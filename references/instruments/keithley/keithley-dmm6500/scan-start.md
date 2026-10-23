# pymeasure.instruments.keithley.KeithleyDMM6500.scan_start

[Owning PyMeasure class, adapter and connection contract](overview.md)

scan_start(*block_communication=True*, *count=None*, *interval=None*)

Start the scanner card so it closes each channel in `scan_channels` sequentially and performs measurements.

If `scan_count` is greater than 1, another scan begins after `scan_interval` second. Scans with large counts or long intervals can take significant time. Prefer `block_communication=False`, then poll `scan_iscomplete` to determine whether measurement has finished.

Parameters:

- **block_communication**: Bool controlling the communication state during scanning. Default is `True`; communication waits for commands to complete before accepting new commands (default: `True`)

- **count**: Alternate way to set `scan_count` before scanning. (default: `None`)

- **interval**: Alternate way to set `scan_interval` in second before scanning. (default: `None`)

Returns:

None
