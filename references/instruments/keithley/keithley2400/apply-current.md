# pymeasure.instruments.keithley.Keithley2400.apply_current

[Owning PyMeasure class, adapter and connection contract](overview.md)

apply_current(*current_range=None*, *compliance_voltage=0.1*)

Set the instrument to source current, using auto range unless `current_range` is supplied, and configure the compliance voltage.

Parameters:

- **compliance_voltage** — Float value in the valid `compliance_voltage` range (default: `0.1`)

- **current_range** — A `current_range` value, or None (default: `None`)

Deprecated since version 0.16: Configure - source mode with `source_mode`. - source current range with `source_current_range` or `source_current_range_auto_enabled`. - compliance voltage with `compliance_voltage`
