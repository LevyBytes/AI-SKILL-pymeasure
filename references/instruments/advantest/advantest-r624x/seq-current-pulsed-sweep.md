# pymeasure.instruments.advantest.advantestR624X.seq_current_pulsed_sweep

[Owning PyMeasure class, adapter and connection contract](../advantest-r624x-sequence-wait-mode/overview.md)

pymeasure.instruments.advantest.advantestR624X.seq_current_pulsed_sweep(*channel*, *sweep_mode*, *repeat*, *current_range*, *base*, *start_value*, *stop_value*, *steps*, *voltage_compliance*, *bias=0*)

Create the command string for PWI (pulsed current sweep).

Parameters:

- **channel** (*int*) — Channel identifier (1=A, 2=B).

- **sweep_mode** (int or `SweepMode`) — Sweep mode selection.

- **repeat** (*int*) – Number of repeats (0-1024).

- **current_range** (int or `CurrentRange`) — Source range for current.

- **base** (*float*) – Base current value.

- **start_value** (*float*) – Start current value.

- **stop_value** (*float*) – Stop current value.

- **steps** (*int*) – Number of steps (2-2048).

- **voltage_compliance** (*float*) – Voltage compliance value.

- **bias** (*float*) – Bias value (default 0).

Return type:

str
