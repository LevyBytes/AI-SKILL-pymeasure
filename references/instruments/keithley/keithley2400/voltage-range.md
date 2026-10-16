# pymeasure.instruments.keithley.Keithley2400.voltage_range

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *voltage_range*: Any*

Set the voltage measurement range in Volts (float, strictly from -210 to 210).

When assigned, the instrument chooses the most sensitive range that can hold the set value, and `voltage_range_auto_enabled` is set to False.
