# pymeasure.instruments.keithley.Keithley2000.complete

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *complete*: Any*

Get the synchronization bit.

Use this property to coordinate a controller with a device. After all selected pending device operations finish, the Operation Complete query inserts ASCII character 1 in the device Output Queue.
