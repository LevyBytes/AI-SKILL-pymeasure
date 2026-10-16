# pymeasure.instruments.proterial.ROD4.complete

This contract is documented in [PyMeasure v0.16.0](https://github.com/pymeasure/pymeasure/blob/v0.16.0/pymeasure/instruments/instrument.py). It is absent from the current development source; check the installed release before using it.

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *complete

Get the synchronization bit.

Use this property to synchronize a controller with a device. Once all selected pending operations finish, the Operation Complete query queues ASCII character 1 in the device Output Queue.
