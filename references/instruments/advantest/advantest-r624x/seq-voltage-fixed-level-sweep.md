# pymeasure.instruments.advantest.advantestR624X.seq_voltage_fixed_level_sweep

[Owning PyMeasure class, adapter and connection contract](../advantest-r624x-sequence-wait-mode/overview.md)

pymeasure.instruments.advantest.advantestR624X.seq_voltage_fixed_level_sweep(*channel*, *voltage_range*, *voltage_level*, *measurement_count*, *current_compliance*, *bias=0*)

Create the command string for FXV (fixed level voltage sweep).

Parameters:

- **channel** (*int*): Channel identifier (1=A, 2=B).

- **voltage_range** (int or `VoltageRange`): Source range for voltage.

- **voltage_level** (*float*) – Voltage level value.

- **measurement_count** (*int*): Count of measurements.

- **current_compliance** (*float*) – Current compliance value.

- **bias** (*float*) – Bias value (default 0).

Return type:

str
