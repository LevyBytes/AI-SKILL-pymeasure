# pymeasure.instruments.signalrecovery.DSP7225.complete

This contract is documented in [PyMeasure v0.16.0](https://github.com/pymeasure/pymeasure/blob/v0.16.0/pymeasure/instruments/instrument.py). It is absent from the current development source; check the installed release before using it.

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *complete

Get the synchronization bit.

Use this property to synchronize a controller with a device. The Operation Complete query puts ASCII character 1 in the device’s Output Queue once every pending selected device operation has finished.
