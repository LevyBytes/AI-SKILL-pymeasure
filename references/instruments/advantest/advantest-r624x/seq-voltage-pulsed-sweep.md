# pymeasure.instruments.advantest.advantestR624X.seq_voltage_pulsed_sweep

[Owning PyMeasure class, adapter and connection contract](../advantest-r624x-sequence-wait-mode/overview.md)

pymeasure.instruments.advantest.advantestR624X.seq_voltage_pulsed_sweep(*channel*, *sweep_mode*, *repeat*, *voltage_range*, *base*, *start_value*, *stop_value*, *steps*, *current_compliance*, *bias=0*)

Create the command string for PWV (pulsed voltage sweep).

Parameters:

- **channel** (*int*) — Channel identifier (1=A, 2=B).

- **sweep_mode** (int or `SweepMode`) — Sweep mode selection.

- **repeat** (*int*) – Number of repeats (0-1024).

- **voltage_range** (int or `VoltageRange`) — Source range for voltage.

- **base** (*float*) – Base voltage value.

- **start_value** (*float*) – Start voltage value.

- **stop_value** (*float*) – Stop voltage value.

- **steps** (*int*) – Number of steps (2-2048).

- **current_compliance** (*float*) – Current compliance value.

- **bias** (*float*) – Bias value (default 0).

Return type:

str
