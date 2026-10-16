# pymeasure.instruments.yokogawa.Yokogawa7651.ramp_to_current

[Owning PyMeasure class, adapter and connection contract](overview.md)

ramp_to_current(*current*, *steps=25*, *duration=0.5*)

Ramp current to a value in Amps by moving through linearly spaced current steps over a duration in seconds.

Parameters:

- **steps** – Number of linear steps to traverse (default: `25`)

- **duration** – Ramp time in seconds (default: `0.5`)
