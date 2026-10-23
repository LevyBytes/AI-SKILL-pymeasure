# pymeasure.instruments.advantest.advantestR624X.seq_current_fixed_level_sweep

[Owning PyMeasure class, adapter and connection contract](../advantest-r624x-sequence-wait-mode/overview.md)

pymeasure.instruments.advantest.advantestR624X.seq_current_fixed_level_sweep(*channel*, *current_range*, *current_level*, *measurement_count*, *voltage_compliance*, *bias=0*)

Create the command string for FXI (fixed level current sweep).

Parameters:

- **channel** (*int*): Channel identifier (1=A, 2=B).

- **current_range** (int or `CurrentRange`): Source range for current.

- **current_level** (*float*) – Current level value.

- **measurement_count** (*int*): Count of measurements.

- **voltage_compliance** (*float*) – Voltage compliance value.

- **bias** (*float*) – Bias value (default 0).

Return type:

str
