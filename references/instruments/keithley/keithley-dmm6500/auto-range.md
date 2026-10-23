# pymeasure.instruments.keithley.KeithleyDMM6500.auto_range

[Owning PyMeasure class, adapter and connection contract](overview.md)

auto_range(*mode=None*)

Enable auto-range for the active mode, or pass a mode name to configure another mode.

Autorange support covers these modes: `current` (DC) and `current ac`; `voltage` (DC) and `voltage ac`; `resistance` (2-wire) and `resistance 4W` (4-wire); plus `capacitance` and `voltage ratio`. Selecting any other mode leaves the instrument unchanged.

Parameters:

**mode**: A valid `mode` name, or None to use the active mode (default: `None`)
