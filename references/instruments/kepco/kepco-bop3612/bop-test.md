# pymeasure.instruments.kepco.KepcoBOP3612.bop_test

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *bop_test*: Any*

Return the error code from a full power supply self-test.

Returns 0 when every test passes; otherwise returns the manual?s matching error code. Caution: disconnect any load before testing, because Output will switch on and swing to maximum values.
