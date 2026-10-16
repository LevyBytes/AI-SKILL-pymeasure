# pymeasure.instruments.advantest.advantestR624X.AdvantestR624X.store_sequence_command

[Owning PyMeasure class, adapter and connection contract](overview.md)

store_sequence_command(*line*, *command*)

Store a command string at a specified sequence program line (`ST`).

Parameters:

- **line** (*int*) – Line number for the memory location

- **command** (*str*) – Command or commands to store, separated by semicolon (;)
