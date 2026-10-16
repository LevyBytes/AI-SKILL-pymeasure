# pymeasure.instruments.agilent.AgilentE4980.aperture

[Owning PyMeasure class, adapter and connection contract](overview.md)

aperture(*time=None*, *averages=1*)

Set and get aperture.

Parameters:

- **time** - integration-time setting supplied as a string: SHORT, MED, or LONG; matching ignores case. Use `None` to read the current values (default: `None`).

- **averages** - numeric count of readings to average together (default: `1`).
