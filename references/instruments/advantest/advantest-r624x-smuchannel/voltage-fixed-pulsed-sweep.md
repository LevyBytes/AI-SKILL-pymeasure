# pymeasure.instruments.advantest.advantestR624X.SMUChannel.voltage_fixed_pulsed_sweep

[Owning PyMeasure class, adapter and connection contract](overview.md)

voltage_fixed_pulsed_sweep(*voltage_range*, *pulse*, *base*, *measurement_count*, *current_compliance*, *bias=0*)

For `PXV`, configure bias value, current compliance, number of measurements, base value, pulse value, and the fixed pulse (voltage) sweep generation range.

Note

The instrument applies current compliance to both polarities (+ and -), regardless of the polarity supplied. It also selects the smallest current compliance range that can contain the configured value.

Warning

For pulsed sweeps, `measure_current()` must be used with a fixed range, for example `CurrentRange.FIXED_BEST`. Auto ranges are unsupported and cause error 00211.
