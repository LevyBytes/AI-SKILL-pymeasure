# pymeasure.instruments.srs.SR510.phase

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *phase*: Any*

Float property for the SR510 phase offset between reference and input, in degrees. Queries return values between -180 and 180 degrees. The settable range is -999 to 999 degrees, with set values internally mapped in the lockin to -180 and 180 degrees.
