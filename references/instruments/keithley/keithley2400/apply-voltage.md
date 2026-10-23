# pymeasure.instruments.keithley.Keithley2400.apply_voltage

[Owning PyMeasure class, adapter and connection contract](overview.md)

apply_voltage(*voltage_range=None*, *compliance_current=0.1*)

Set the instrument to source voltage, using auto range unless `voltage_range` is supplied, and configure the compliance current.

Parameters:

- **compliance_current**: Float value in the valid `compliance_current` range (default: `0.1`)

- **voltage_range**: A `voltage_range` value, or None (default: `None`)

Deprecated since version 0.16: Prefer configuring - source mode with `source_mode`. - source voltage range with `source_voltage_range` or `source_voltage_range_auto_enabled`. - compliance current with `compliance_current`

## Related property contracts

- Open when checking pymeasure.instruments.keithley.Keithley2400.arm_count: [arm_count](arm-count.md).
