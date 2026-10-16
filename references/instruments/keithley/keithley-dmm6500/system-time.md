# pymeasure.instruments.keithley.KeithleyDMM6500.system_time

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *system_time*: Any*

Set or read the instrument system time. Accepted set formats are `year, month, day, hour, minute, second` or `hour, minute, second`. Example using the `time` package to set the instrument clock: `dmm.system_time = time.strftime("%Y, %m, %d, %H, %M, %S")`
