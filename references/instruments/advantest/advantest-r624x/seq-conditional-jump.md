# pymeasure.instruments.advantest.advantestR624X.seq_conditional_jump

[Owning PyMeasure class, adapter and connection contract](../advantest-r624x-sequence-wait-mode/overview.md)

pymeasure.instruments.advantest.advantestR624X.seq_conditional_jump(*channel*, *condition*, *destination*)

Create the command string for EXT (conditional jump).

Parameters:

- **channel** (*int*): Channel selector (1=A, 2=B, 3=A|B OR).

- **condition** (int or `JumpCondition`): Jump condition selector.

- **destination** (*int*) – Jump destination program number (1-20).

Return type:

str
