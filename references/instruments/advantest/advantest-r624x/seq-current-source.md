# pymeasure.instruments.advantest.advantestR624X.seq_current_source

[Owning PyMeasure class, adapter and connection contract](../advantest-r624x-sequence-wait-mode/overview.md)

pymeasure.instruments.advantest.advantestR624X.seq_current_source(*channel*, *source_range*, *source_value*, *compliance*)

Create the command string for DI (DC current source).

Parameters:

- **channel** (*int*): Channel identifier (1=A, 2=B).

- **source_range** (int or `CurrentRange`): Source range for current.

- **source_value** (*float*) – Source current value.

- **compliance** (*float*) – Voltage compliance value.

Return type:

str
