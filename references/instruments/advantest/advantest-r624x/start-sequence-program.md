# pymeasure.instruments.advantest.advantestR624X.AdvantestR624X.start_sequence_program

[Owning PyMeasure class, adapter and connection contract](overview.md)

start_sequence_program(*start*, *stop*, *repeat*)

Run the sequence program from the start line through the stop line, with the requested repeats (`RU`).

Parameters:

- **start** (*int*) – Program number to start from, ranging 1 to 100

- **stop** (*int*) – Program number to stop at, ranging from 1 to 100

- **repeat** (*int*) – Number of repetitions, from 1 to 100
