# pymeasure.instruments.keysight.KeysightDSOX1102G.timebase_setup

[Owning PyMeasure class, adapter and connection contract](overview.md)

timebase_setup(*mode=None*, *offset=None*, *horizontal_range=None*, *scale=None*)

Configure the timebase. Parameters that are not provided stay unchanged. Changing one parameter can affect others. Consult the oscilloscope documentation and, when needed, make several consecutive channel_setup calls.

Parameters:

- **mode** – Timebase mode; valid values are “main”, “window”, “xy”, or “roll”. (default: `None`)

- **offset** – Seconds of offset between the trigger and the screen center. (default: `None`)

- **horizontal_range** – Full-scale range, in seconds. (default: `None`)

- **scale** – Seconds per division. (default: `None`)

## Related property contracts

- Open when checking pymeasure.instruments.keysight.KeysightDSOX1102G.waveform_data: [waveform_data](waveform-data.md).
