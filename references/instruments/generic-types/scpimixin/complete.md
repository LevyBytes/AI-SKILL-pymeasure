# pymeasure.instruments.generic_types.SCPIMixin.complete

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *complete*: Any*

Get the synchronization bit.

Use this property to synchronize a controller with a device. Once all selected pending operations finish, the Operation Complete query queues ASCII character 1 in the device Output Queue.
