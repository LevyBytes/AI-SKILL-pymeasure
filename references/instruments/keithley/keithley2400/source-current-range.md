# pymeasure.instruments.keithley.Keithley2400.source_current_range

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *source_current_range*: Any*

Configure the range used for sourced current, in Amps. Accepted float values are strictly from -1.05 to 1.05.

When assigned, the instrument chooses the most sensitive range that can hold the set value, and Auto-range is disabled.
