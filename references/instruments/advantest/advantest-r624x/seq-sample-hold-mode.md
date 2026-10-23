# pymeasure.instruments.advantest.advantestR624X.seq_sample_hold_mode

[Owning PyMeasure class, adapter and connection contract](../advantest-r624x-sequence-wait-mode/overview.md)

pymeasure.instruments.advantest.advantestR624X.seq_sample_hold_mode(*channel*, *mode*)

Create the command string for MST (sample/hold mode).

Parameters:

- **channel** (*int*): Channel identifier (1=A, 2=B).

- **mode** (int or `SampleHold`): Integration time mode selection.

Return type:

str
