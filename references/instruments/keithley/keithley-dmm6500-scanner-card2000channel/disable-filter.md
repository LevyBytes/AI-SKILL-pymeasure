# pymeasure.instruments.keithley.keithleyDMM6500.ScannerCard2000Channel.disable_filter

[Owning PyMeasure class, adapter and connection contract](overview.md)

disable_filter(*mode=None*)

Turn off the averaging filter on the active mode, or specify another mode by name.

Parameters:

**mode** - Supply a valid `mode` name, or pass None to use the active mode (default: `None`)

Returns:

A filter status value returned by the instrument
