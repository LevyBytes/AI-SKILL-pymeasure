# pymeasure.instruments.anritsu.anritsuMS464xB.Trace.measurement_parameter

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *measurement_parameter*: Any*

Set the measurement parameter for the indicated trace.

Accepted values include any 4-port S-parameter, such as S11, S12, or S41, or one item from this list:

| value | description |
| --- | --- |
| Sxx | S-parameters (1-4 for both x) |
| MIX | Response Mixed Mode |
| NFIG | Noise Figure trace response (available only with option 41 or 48) |
| NPOW | Noise Power trace response (available only with option 41 or 48) |
| NTEMP | Noise Temperature trace response (available only with option 41 or 48) |
| AGA | Noise Figure Available Gain trace response (available only with option 48) |
| IGA | Noise Figure Insertion Gain trace response (available only with option 48) |
