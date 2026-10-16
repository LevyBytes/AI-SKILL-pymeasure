# pymeasure.instruments.advantest.advantestR624X.SMUChannel.set_timing_parameters

[Owning PyMeasure class, adapter and connection contract](overview.md)

set_timing_parameters(*hold_time*, *measurement_delay*, *pulsed_width*, *pulsed_period*)

Configure hold time, measurement delay, pulse width, and pulse period (`WT`).

Parameters:

- **hold_time** (*float*) – Duration of the full pulse cycle before the next pulse

- **measurement_delay** (*float*) – Interval from one measurement to the next

- **pulsed_width** (*float*) – Pulse-width time setting

- **pulsed_period** (*float*) – Pulse-period time setting

Note

Pulse measurement restrictions depend on the pulse period (Tp) setting listed below. These limits do not apply to pulse sweep measurements.
- Tp < 2ms : Not measured.

- 2ms <= Tp < 10ms : Measure once every 5 ~ 20ms.

- 10ms <= Tp: a measurement is taken whenever a pulse is generated.
