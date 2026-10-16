# pymeasure.instruments.keithley.Keithley2450.apply_current

[Owning PyMeasure class, adapter and connection contract](overview.md)

apply_current(*current_range=None*, *compliance_voltage=0.1*)

Sets the instrument up to source current, using auto range unless a current range is provided, and sets the compliance voltage.

Parameters:

- **compliance_voltage** - Float within the allowed `compliance_voltage` range (default: `0.1`)

- **current_range** - `current_range` value, or None (default: `None`)
