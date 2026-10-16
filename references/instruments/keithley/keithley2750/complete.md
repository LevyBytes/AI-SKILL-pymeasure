# pymeasure.instruments.keithley.Keithley2750.complete

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *complete*: Any*

Get the synchronization bit.

This property coordinates a controller with the device. Once all pending selected device operations finish, the Operation Complete query inserts ASCII character 1 into the device's Output Queue.
