# pymeasure.instruments.keithley.Keithley2400.complete

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *complete*: Any*

Get the synchronization bit.

Use this property to synchronize a controller with a device. After all selected pending device operations finish, the Operation Complete query puts ASCII character 1 in the device's Output Queue.
