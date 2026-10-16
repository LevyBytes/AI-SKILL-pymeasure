# pymeasure.instruments.danfysik.Danfysik8500.set_ramp_to_current

[Owning PyMeasure class, adapter and connection contract](overview.md)

set_ramp_to_current(*current*, *points*, *delay_time=1*)

Configure a linear ramp from the initial current to another current, using a point count and delay time.

Parameters:

- **current** – Final current in Amps

- **points** – Number of linear points to traverse

- **delay_time** – Delay time in seconds (default: `1`)
