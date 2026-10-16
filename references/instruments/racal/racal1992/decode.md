# pymeasure.instruments.racal.Racal1992.decode

[Owning PyMeasure class, adapter and connection contract](overview.md)

*static *decode(*v*, *allowed_types=None*)

Decode received message.

Returned values all share one layout: a 2-letter type prefix followed by a floating point number, which may of course represent an integer. For example, math constant Z is reported as MZ+001.00000000E+00
