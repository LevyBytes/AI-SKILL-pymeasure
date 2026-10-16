# pymeasure.instruments.tdk.tdk_gen40_38.TDK_Gen40_38.complete

This inherited contract is documented in [PyMeasure v0.16.0](https://github.com/pymeasure/pymeasure/blob/v0.16.0/pymeasure/instruments/instrument.py). Check the installed release before using it.

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *complete

Get the synchronization bit.

This property synchronizes a controller with a device. The Operation Complete query writes ASCII character 1 to the device’s Output Queue once every pending selected device operation is complete.
