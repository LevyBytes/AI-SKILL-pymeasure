# pymeasure.instruments.advantest.advantestR624X.seq_current_pulsed_source

[Owning PyMeasure class, adapter and connection contract](../advantest-r624x-sequence-wait-mode/overview.md)

pymeasure.instruments.advantest.advantestR624X.seq_current_pulsed_source(*channel*, *source_range*, *pulse_value*, *base_value*, *compliance*)

Create the command string for PI (pulsed current source).

Parameters:

- **channel** (*int*) — Channel identifier (1=A, 2=B).

- **source_range** (int or `CurrentRange`) — Source range for current.

- **pulse_value** (*float*) – Pulse current value.

- **base_value** (*float*) – Base current value.

- **compliance** (*float*) – Voltage compliance value.

Return type:

str
