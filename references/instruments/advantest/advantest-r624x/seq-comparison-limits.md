# pymeasure.instruments.advantest.advantestR624X.seq_comparison_limits

[Owning PyMeasure class, adapter and connection contract](../advantest-r624x-sequence-wait-mode/overview.md)

pymeasure.instruments.advantest.advantestR624X.seq_comparison_limits(*channel*, *comparison*, *voltage_value*, *upper_limit*, *lower_limit*)

Create the command string for CMD (comparison limits).

Parameters:

- **channel** (*int*): Channel identifier (1=A, 2=B).

- **comparison** (*bool*): Turn comparison on or off (True=ON, False=OFF).

- **voltage_value** (*bool*): Set True for voltage and False for current.

- **upper_limit** (*float*) – Upper comparison limit.

- **lower_limit** (*float*) – Lower comparison limit.

Return type:

str
