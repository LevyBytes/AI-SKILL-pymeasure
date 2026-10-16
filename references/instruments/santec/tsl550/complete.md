# pymeasure.instruments.santec.tsl550.TSL550.complete

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *complete*: Any*

Get the synchronization bit.

Use this property to coordinate controller and device timing. The Operation Complete query writes ASCII character 1 to the device's Output Queue once every pending selected device operation is done.
