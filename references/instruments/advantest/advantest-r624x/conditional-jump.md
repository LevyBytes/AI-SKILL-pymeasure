# pymeasure.instruments.advantest.advantestR624X.AdvantestR624X.conditional_jump

[Owning PyMeasure class, adapter and connection contract](overview.md)

conditional_jump(*channel*, *condition*, *destination*)

Configure a conditional jump for a high-speed sequence program (`EXT`).

Parameters:

- **channel** (*int*) – Selects channel 1=A, 2=B, or 3=A|B OR condition.

- **condition** (int or `JumpCondition`) – Jump condition selector.

- **destination** (*int*) – Destination program number for the jump (1 to 20).

Note

- Conditions 1-4: continue to the next program when the condition is not met.

- Conditions 7-10: remain at the current program when the condition is not met.

- Condition 5: cancel conditional jump.

- Condition 6: perform an unconditional jump; channel data is ignored.

- The destination must be >= current program number to run.
