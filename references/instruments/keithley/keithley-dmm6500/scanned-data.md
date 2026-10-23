# pymeasure.instruments.keithley.KeithleyDMM6500.scanned_data

[Owning PyMeasure class, adapter and connection contract](overview.md)

scanned_data(*start_idx=None*, *end_idx=None*, *raw=False*)

Return scan values from the buffer as a list.

Parameters:

- **start_idx**: Bool value controlling communication state during scanning. Default is `True`, meaning communication waits for command completion before new commands are accepted (default: `None`)

- **end_idx**: Alternate way to set `scan_count` (default: `None`)

- **raw**: Alternate way to set `scan_interval` in second (default: `False`)

Returns:

List of measured scan-channel values

Return type:

A list of channels’ list
