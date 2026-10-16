# pymeasure.instruments.keithley.KeithleyDMM6500.aperture

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *aperture*: Any*

Manage the aperture time for the currently active `mode`.

Accepted values are `MIN`, `DEF`, `MAX`, or a number from 8.333u through 0.25 s.

Note

Aperture configuration applies to `voltage`, `current`, `resistance`, and `resistance 4W`; it also applies to `diode`, `temperature`, `frequency`, `period`, and `voltage ratio` mode. If the active mode has no aperture support, the command waits for the adapter timeout and then raises -113 "Undefined header".
