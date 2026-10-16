# pymeasure.instruments.advantest.advantestR624X.seq_measure_voltage

[Owning PyMeasure class, adapter and connection contract](../advantest-r624x-sequence-wait-mode/overview.md)

pymeasure.instruments.advantest.advantestR624X.seq_measure_voltage(*channel*, *enable=True*, *internal_measurement=True*, *voltage_range=VoltageRange.AUTO*)

Create the command string for RV (voltage measurement).

Parameters:

- **channel** (*int*) — Channel identifier (1=A, 2=B).

- **enable** (*bool*) – Enable voltage measurement.

- **internal_measurement** (*bool*) — Select the internal measurement input.

- **voltage_range** (int or `VoltageRange`) — Measurement range for voltage. (default: `<VoltageRange.AUTO: 0>`)

Return type:

str
