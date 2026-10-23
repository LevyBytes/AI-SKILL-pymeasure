# pymeasure.instruments.advantest.advantestR624X.seq_timing_parameters

[Owning PyMeasure class, adapter and connection contract](../advantest-r624x-sequence-wait-mode/overview.md)

pymeasure.instruments.advantest.advantestR624X.seq_timing_parameters(*channel*, *hold_time*, *measurement_delay*, *pulsed_width*, *pulsed_period*)

Create the command string for WT (timing parameters).

Parameters:

- **channel** (*int*): Channel identifier (1=A, 2=B).

- **hold_time** (*float*): Hold interval, in seconds.

- **measurement_delay** (*float*): Measurement delay interval, in seconds.

- **pulsed_width** (*float*): Pulse width, in seconds.

- **pulsed_period** (*float*): Pulse period, in seconds.

Return type:

str
