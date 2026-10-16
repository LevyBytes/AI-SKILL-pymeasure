# pymeasure.instruments.anritsu.anritsuMS464xB.MeasurementChannel.sweep_type

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *sweep_type*: Any*

Set the sweep type for the indicated channel.

Valid options are:

| value | description |
| --- | --- |
| LIN | Frequency-based linear sweep |
| LOG | Frequency-based logarithmic sweep |
| FSEGM | Segment-based sweep using frequency-based segments |
| ISEGM | Index-based sweep using frequency-based segments |
| POW | Power-based sweep using either a CW frequency or swept-frequency |
| MFGC | Multiple frequency gain compression |
