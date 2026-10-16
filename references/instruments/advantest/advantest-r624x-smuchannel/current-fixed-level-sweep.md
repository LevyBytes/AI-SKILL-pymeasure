# pymeasure.instruments.advantest.advantestR624X.SMUChannel.current_fixed_level_sweep

[Owning PyMeasure class, adapter and connection contract](overview.md)

current_fixed_level_sweep(*current_range*, *current_level*, *measurement_count*, *voltage_compliance*, *bias=0*)

For `FXI`, configure bias value, voltage compliance, level value, and the fixed level sweep (current) generation range.

Note

Voltage compliance is set for both polarities (+ and -), regardless of the polarity supplied. The instrument chooses the smallest voltage compliance range that contains the configured value.
