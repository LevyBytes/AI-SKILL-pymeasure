# pymeasure.instruments.keithley.Keithley2400Legacy.apply_current

[Owning PyMeasure class, adapter and connection contract](overview.md)

apply_current(*current_range=None*, *compliance_voltage=0.1*)

Set up the instrument for source current, choosing auto range unless a current range is supplied. Also sets the compliance voltage.

Parameters:

- **compliance_voltage** - float value within the valid range for `compliance_voltage` (default: `0.1`)

- **current_range** - `current_range` value, or None (default: `None`)
