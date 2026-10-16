# pymeasure.instruments.advantest.advantestR624X.AdvantestR624X.query_sequence_program

[Owning PyMeasure class, adapter and connection contract](overview.md)

query_sequence_program(*line*)

Query the command text stored at a sequence program line (`LST?`).

Parameters:

**line** (*int*) – Line number naming the memory location to read.

Returns:

Commands stored in sequence memory.

Return type:

str
