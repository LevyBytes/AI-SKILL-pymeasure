# pymeasure.instruments.attocube.anc300.Axis.stepd

This contract is documented in [PyMeasure v0.16.0](https://github.com/pymeasure/pymeasure/blob/v0.16.0/pymeasure/instruments/attocube/anc300.py). It is absent from the current development source; check the installed release before using it.

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *stepd*: Any*

Command N downward steps. Use mode `stp`; N must be positive. A value of 0 starts continuous movement and continues until stop is called.

Deprecated since version 0.13.0: Use meth:move_raw in new code.
