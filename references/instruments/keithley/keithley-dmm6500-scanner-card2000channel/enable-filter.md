# pymeasure.instruments.keithley.keithleyDMM6500.ScannerCard2000Channel.enable_filter

[Owning PyMeasure class, adapter and connection contract](overview.md)

enable_filter(*mode=None*, *type='repeat'*, *count=1*)

Turn on the averaging filter on the active mode, or specify another mode by name.

Parameters:

- **mode** - Supply a valid `mode` name, or pass None to use the active mode (default: `None`)

- **type** - Averaging filter type; accepted choices are `REPeat`, `MOVing`, or `HYBRid`. (default: `'repeat'`)

- **count** - Number of averages; allowed values range from 1 to 100 (default: `1`)

Returns:

A filter status value returned by the instrument
