# pymeasure.instruments.signalrecovery.DSP7225.sensitivity

This contract is documented in [PyMeasure v0.16.0](https://github.com/pymeasure/pymeasure/blob/v0.16.0/pymeasure/instruments/instrument.py). It is absent from the current development source; check the installed release before using it.

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *sensitivity

Control the measurement sensitivity range for the signal.

Voltage measurement mode accepts discrete values from 2 nV to 1 V. Current measurement mode accepts discrete values starting at 2 fA and ending at 1 µA for normal current mode; low noise current mode extends up to 10 nA.
