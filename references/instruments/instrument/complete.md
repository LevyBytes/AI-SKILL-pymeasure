# pymeasure.instruments.Instrument.complete

This contract is documented in [PyMeasure v0.16.0](https://github.com/pymeasure/pymeasure/blob/v0.16.0/pymeasure/instruments/instrument.py). It is absent from the current development source; check the installed release before using it.

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *complete

Get the synchronization bit.

This property synchronizes a controller with a device. The Operation Complete query puts ASCII character 1 into the device's Output Queue after all pending selected device operations have completed.
