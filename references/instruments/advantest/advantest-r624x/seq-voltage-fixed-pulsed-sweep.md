# pymeasure.instruments.advantest.advantestR624X.seq_voltage_fixed_pulsed_sweep

[Owning PyMeasure class, adapter and connection contract](../advantest-r624x-sequence-wait-mode/overview.md)

pymeasure.instruments.advantest.advantestR624X.seq_voltage_fixed_pulsed_sweep(*channel*, *voltage_range*, *pulse*, *base*, *measurement_count*, *current_compliance*, *bias=0*)

Create the command string for PXV (fixed pulsed voltage sweep).

Parameters:

- **channel** (*int*) — Channel identifier (1=A, 2=B).

- **voltage_range** (int or `VoltageRange`) — Source range for voltage.

- **pulse** (*float*) – Pulse voltage value.

- **base** (*float*) – Base voltage value.

- **measurement_count** (*int*) — Count of measurements.

- **current_compliance** (*float*) – Current compliance value.

- **bias** (*float*) – Bias value (default 0).

Return type:

str
