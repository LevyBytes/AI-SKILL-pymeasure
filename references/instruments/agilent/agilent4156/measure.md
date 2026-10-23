# pymeasure.instruments.agilent.agilent4156.Agilent4156.measure

[Owning PyMeasure class, adapter and connection contract](overview.md)

measure(*period='INF'*, *points=100*)

Run one sweep-mode measurement and wait until it finishes.

For sampling mode, both measurement period and number of points may be provided.

Parameters:

- **period**: Sampling measurement period, from 6E-6 to 1E11 seconds. Default setting is `INF`. (default: `'INF'`)

- **points**: Sample count to measure, from 1 to 10001. Default setting is `100`. (default: `100`)
