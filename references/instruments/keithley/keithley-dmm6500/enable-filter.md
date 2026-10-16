# pymeasure.instruments.keithley.KeithleyDMM6500.enable_filter

[Owning PyMeasure class, adapter and connection contract](overview.md)

enable_filter(*mode=None*, *type='repeat'*, *count=1*)

Turn on the averaging filter for the active mode, or pass a mode name to affect another mode.

Parameters:

- **mode** — A valid `mode` name, or None to use the active mode (default: `None`)

- **type** — Averaging filter type; valid choices are `REPeat`, `MOVing`, or `HYBRid`. (default: `'repeat'`)

- **count** — Number of averages, with allowed values from 1 to 100 (default: `1`)

Returns:

Filter status returned by the instrument
