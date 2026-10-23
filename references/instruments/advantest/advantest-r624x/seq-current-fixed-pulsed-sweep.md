# pymeasure.instruments.advantest.advantestR624X.seq_current_fixed_pulsed_sweep

[Owning PyMeasure class, adapter and connection contract](../advantest-r624x-sequence-wait-mode/overview.md)

pymeasure.instruments.advantest.advantestR624X.seq_current_fixed_pulsed_sweep(*channel*, *current_range*, *pulse*, *base*, *measurement_count*, *voltage_compliance*, *bias=0*)

Create the command string for PXI (fixed pulsed current sweep).

Parameters:

- **channel** (*int*): Channel identifier (1=A, 2=B).

- **current_range** (int or `CurrentRange`): Source range for current.

- **pulse** (*float*) – Pulse current value.

- **base** (*float*) – Base current value.

- **measurement_count** (*int*): Count of measurements.

- **voltage_compliance** (*float*) – Voltage compliance value.

- **bias** (*float*) – Bias value (default 0).

Return type:

str
