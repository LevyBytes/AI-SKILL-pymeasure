# pymeasure.instruments.keithley.Keithley2700.complete

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *complete*: Any*

Get the synchronization bit.

Use this property to synchronize the controller with the device. After all pending selected device operations finish, the Operation Complete query puts ASCII character 1 in the Output Queue of the device.
