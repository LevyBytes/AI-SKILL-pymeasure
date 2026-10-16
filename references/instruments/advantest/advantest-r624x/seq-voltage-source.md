# pymeasure.instruments.advantest.advantestR624X.seq_voltage_source

[Owning PyMeasure class, adapter and connection contract](../advantest-r624x-sequence-wait-mode/overview.md)

pymeasure.instruments.advantest.advantestR624X.seq_voltage_source(*channel*, *source_range*, *source_value*, *compliance*)

Create the command string for DV (DC voltage source).

Parameters:

- **channel** (*int*) — Channel identifier (1=A, 2=B).

- **source_range** (int or `VoltageRange`) — Source range for voltage.

- **source_value** (*float*) – Source voltage value.

- **compliance** (*float*) – Current compliance value.

Return type:

str
