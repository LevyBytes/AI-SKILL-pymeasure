# pymeasure.instruments.agilent.agilentB1500.SPGUChannel.get_pulse_timings

[Owning PyMeasure class, adapter and connection contract](overview.md)

get_pulse_timings(*source=1*)

Read SPGU channel timing parameters. (`SPT?`)

Before pulse timings are read, place SPGU operating mode in PG with `SIM 0`.

Parameters:

**source** (*SPGUSignalSource** or **int*) - Pulse timing signal source; default is `SPGUSignalSource.PULSE_SIGNAL_1`

Returns:

Returns (delay, width, rise_time, fall_time) as a tuple

Return type:

tuple
