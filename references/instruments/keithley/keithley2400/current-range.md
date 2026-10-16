# pymeasure.instruments.keithley.Keithley2400.current_range

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *current_range*: Any*

Set the current measurement range in Amps (float, strictly from -1.05 to 1.05).

When assigned, the instrument chooses the most sensitive range that can hold the set value, and `current_range_auto_enabled` is set to False.
