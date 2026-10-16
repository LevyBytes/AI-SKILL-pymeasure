# pymeasure.instruments.keithley.Keithley2400Legacy.apply_voltage

[Owning PyMeasure class, adapter and connection contract](overview.md)

apply_voltage(*voltage_range=None*, *compliance_current=0.1*)

Set up the instrument for source voltage, choosing auto range unless a voltage range is supplied. Also sets the compliance current.

Parameters:

- **compliance_current** - float value within the valid range for `compliance_current` (default: `0.1`)

- **voltage_range** - `voltage_range` value, or None (default: `None`)
