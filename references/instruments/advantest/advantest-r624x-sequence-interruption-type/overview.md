# pymeasure.instruments.advantest.advantestR624X.SequenceInterruptionType

*class *pymeasure.instruments.advantest.advantestR624X.SequenceInterruptionType(**values*)

Bases: `IntEnum`

1. Release pause state only has effect while the sequence program is in pause state; otherwise, the command is ignored.

2. Pause state is entered after the currently executing program finishes.

3. Abort sequence program halts the sequence program after the program now running finishes. If that program is a sweep operation, the sweep is interrupted and the sequence program stops, with the output set to the bias value.
