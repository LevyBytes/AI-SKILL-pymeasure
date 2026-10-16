# pymeasure.instruments.keithley.Keithley2450.apply_voltage

[Owning PyMeasure class, adapter and connection contract](overview.md)

apply_voltage(*voltage_range=None*, *compliance_current=0.1*)

Sets the instrument up to source voltage, using auto range unless a voltage range is provided, and sets the compliance current.

Parameters:

- **compliance_current** - Float within the allowed `compliance_current` range (default: `0.1`)

- **voltage_range** - `voltage_range` value, or None (default: `None`)
