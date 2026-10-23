# pymeasure.instruments.keithley.KeithleyDMM6500.acquire_relative

[Owning PyMeasure class, adapter and connection contract](overview.md)

acquire_relative(*mode=None*)

Use the active reading as the relative value for the active mode, or provide a mode name to target a different mode.

Parameters:

**mode**: A valid `mode` name, or None to use the active mode (default: `None`)

Returns:

The acquired relative value
