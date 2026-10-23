# pymeasure.instruments.keithley.KeithleyDMM6500.disable_filter

[Owning PyMeasure class, adapter and connection contract](overview.md)

disable_filter(*mode=None*)

Turn off the averaging filter for the active mode, or provide a mode name to affect another mode.

Parameters:

**mode**: A valid `mode` name, or None to use the active mode (default: `None`)

Returns:

Filter status returned by the instrument
