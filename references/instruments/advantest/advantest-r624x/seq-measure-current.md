# pymeasure.instruments.advantest.advantestR624X.seq_measure_current

[Owning PyMeasure class, adapter and connection contract](../advantest-r624x-sequence-wait-mode/overview.md)

pymeasure.instruments.advantest.advantestR624X.seq_measure_current(*channel*, *enable=True*, *internal_measurement=True*, *current_range=CurrentRange.AUTO*)

Create the command string for RI (current measurement).

Parameters:

- **channel** (*int*): Channel identifier (1=A, 2=B).

- **enable** (*bool*) – Enable current measurement.

- **internal_measurement** (*bool*): Select the internal measurement input.

- **current_range** (int or `CurrentRange`): Measurement range for current. (default: `<CurrentRange.AUTO: 0>`)

Return type:

str
