# pymeasure.instruments.advantest.advantestR624X.seq_voltage_pulsed_source

[Owning PyMeasure class, adapter and connection contract](../advantest-r624x-sequence-wait-mode/overview.md)

pymeasure.instruments.advantest.advantestR624X.seq_voltage_pulsed_source(*channel*, *source_range*, *pulse_value*, *base_value*, *compliance*)

Create the command string for PV (pulsed voltage source).

Parameters:

- **channel** (*int*): Channel identifier (1=A, 2=B).

- **source_range** (int or `VoltageRange`): Source range for voltage.

- **pulse_value** (*float*) – Pulse voltage value.

- **base_value** (*float*) – Base voltage value.

- **compliance** (*float*) – Current compliance value.

Return type:

str
