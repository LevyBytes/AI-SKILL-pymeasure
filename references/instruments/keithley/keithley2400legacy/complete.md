# pymeasure.instruments.keithley.Keithley2400Legacy.complete

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *complete*: Any*

Get the synchronization bit.

This property provides synchronization between a controller and a device. The Operation Complete query writes ASCII character 1 into the device's Output Queue after all pending selected device operations are complete.
