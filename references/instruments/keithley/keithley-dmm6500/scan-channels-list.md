# pymeasure.instruments.keithley.KeithleyDMM6500.scan_channels_list

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *scan_channels_list

Convert the `scan_channels` string into a list of integers.

For example, `scan_channels` set to `1,3:5,7:8,10` returns `[1,3,4,5,7,8,10]`. Assigning `scan_channels_list=[1,2,3,4,6]` sets `scan_channels` to `1:4,6`.
