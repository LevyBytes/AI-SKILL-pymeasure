# pymeasure.instruments.signalrecovery.DSP7265.sensitivity

This contract is documented in [PyMeasure v0.16.0](https://github.com/pymeasure/pymeasure/blob/v0.16.0/pymeasure/instruments/instrument.py). It is absent from the current development source; check the installed release before using it.

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *sensitivity

Set the measurement sensitivity range for the signal.

In voltage measurement mode, accepted values are discrete choices spanning 2 nV through 1 V. For current measurement mode, the discrete choices start at 2 fA and extend to 1 µA in normal current mode; in low noise current mode, they extend up to 10 nA.
