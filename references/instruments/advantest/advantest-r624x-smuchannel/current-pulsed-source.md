# pymeasure.instruments.advantest.advantestR624X.SMUChannel.current_pulsed_source

[Owning PyMeasure class, adapter and connection contract](overview.md)

current_pulsed_source(*source_range*, *pulse_value*, *base_value*, *voltage_compliance*)

For pulse (current) measurement (`PI`), configure voltage compliance together with source range, pulse value, and base value.

Note

Voltage compliance is set for both polarities (+ and -), regardless of the polarity supplied. The instrument chooses the smallest voltage compliance range that contains the configured value.

Warning

`source_range` must be a fixed range, for example `CurrentRange.FIXED_BEST`. Pulsed modes do not support `CurrentRange.AUTO` or `AUTO_*` ranges and return error 00211.
