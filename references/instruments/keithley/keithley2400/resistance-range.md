# pymeasure.instruments.keithley.Keithley2400.resistance_range

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *resistance_range*: Any*

Set the resistance range in Ohms (float, strictly from 0 to 210e6).

When assigned, the instrument chooses the most sensitive range that can hold the set value, and `resistance_range_auto_enabled` is set to False.
