# pymeasure.instruments.agilent.agilentB1500.SPGUChannel.set_pulse_timings

[Owning PyMeasure class, adapter and connection contract](overview.md)

set_pulse_timings(*source=1*, *delay=0*, *width=1e-07*, *rise_time=2e-08*, *fall_time=None*)

Configure SPGU channel timing parameters. (`SPT`)

Before assigning pulse timings, set the SPGU operating mode to PG with the `SIM 0` command.

Parameters:

- **source** (*SPGUSignalSource** or **int*) – Pulse-timing signal source, defaults to `SPGUSignalSource.PULSE_SIGNAL_1`

- **delay** (*float*) – Pulse delay in seconds; defaults to 0

- **width** (*float*) – Pulse width in seconds; defaults to 1e-7

- **rise_time** (*float*) – Pulse rise time in seconds; defaults to 2e-8

-
**fall_time** (*float*) - Pulse fall time, in seconds; when None, rise_time is used as the default
