# pymeasure.instruments.keithley.KeithleyDMM6500.auto_range_status

[Owning PyMeasure class, adapter and connection contract](overview.md)

auto_range_status(*mode=None*)

Return whether auto-range is enabled for the active mode, or for a supplied mode name. Supported modes are grouped as `current` (DC) with `current ac`, `voltage` (DC) with `voltage ac`, `resistance` (2-wire) with `resistance 4W` (4-wire), plus `capacitance` and `voltage ratio`; unsupported modes also return `False`.

Parameters:

**mode**: A valid `mode` name, or None to use the active mode (default: `None`)

Returns:

Boolean indicating whether auto-range is enabled

Return type:

bool
