# pymeasure.instruments.advantest.advantestR624X.seq_clear_program

[Owning PyMeasure class, adapter and connection contract](../advantest-r624x-sequence-wait-mode/overview.md)

pymeasure.instruments.advantest.advantestR624X.seq_clear_program(*program_number*, *clear_mode*)

Create the command string for PCEL (program clear).

Parameters:

- **program_number** (*int*) – Program number (1-20).

- **clear_mode** (int or `ProgramClearMode`): Clear mode selector.

Return type:

str
