# pymeasure.instruments.advantest.advantestR624X.SMUChannel.voltage_fixed_level_sweep

[Owning PyMeasure class, adapter and connection contract](overview.md)

voltage_fixed_level_sweep(*voltage_range*, *voltage_level*, *measurement_count*, *current_compliance*, *bias=0*)

For `FXV`, configure bias value, current compliance, level value, and the fixed level sweep (voltage) generation range.

Note

The instrument applies current compliance to both polarities (+ and -), regardless of the polarity supplied. It also selects the smallest current compliance range that can contain the configured value.
