# pymeasure.instruments.keithley.Keithley2200.complete

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *complete*: Any*

Get the synchronization bit.

Use this property to synchronize a controller with a device. When all pending selected device operations are done, the Operation Complete query puts ASCII character 1 in the device’s Output Queue.
