# pymeasure.instruments.advantest.advantestR624X.SMUChannel.voltage_pulsed_source

[Owning PyMeasure class, adapter and connection contract](overview.md)

voltage_pulsed_source(*source_range*, *pulse_value*, *base_value*, *current_compliance*)

For pulse (voltage) measurement (`PV`), configure current compliance together with source range, pulse value, and base value.

Note

The instrument applies current compliance to both polarities (+ and -), regardless of the polarity supplied. It also selects the smallest current compliance range that can contain the configured value.

Warning

For pulsed sources, call `measure_current()` with a fixed range such as `CurrentRange.FIXED_BEST`. Pulsed modes do not support `CurrentRange.AUTO` or `AUTO_*` ranges and return error 00211.
