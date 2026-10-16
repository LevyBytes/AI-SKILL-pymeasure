# pymeasure.instruments.keithley.Keithley2281S.complete

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *complete*: Any*

Get the synchronization bit.

This property synchronizes a controller with a device. After all pending selected device operations finish, the Operation Complete query puts ASCII character 1 in the device’s Output Queue.
