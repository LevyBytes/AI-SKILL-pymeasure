# pymeasure.instruments.advantest.advantestR624X.SMUChannel.current_fixed_pulsed_sweep

[Owning PyMeasure class, adapter and connection contract](overview.md)

current_fixed_pulsed_sweep(*current_range*, *pulse*, *base*, *measurement_count*, *voltage_compliance*, *bias=0*)

For `PXI`, configure bias value, voltage compliance, number of measurements, base value, pulse value, and the fixed pulse (current) sweep generation range.

Note

Voltage compliance is set for both polarities (+ and -), regardless of the polarity supplied. The instrument chooses the smallest voltage compliance range that contains the configured value.

Warning

`current_range` must be a fixed range, for example `CurrentRange.FIXED_BEST`. `CurrentRange.AUTO` and `AUTO_*` ranges are unavailable for pulse sweep and cause error 00211.
