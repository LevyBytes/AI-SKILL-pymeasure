# pymeasure.instruments.advantest.advantestR624X.seq_wait

[Owning PyMeasure class, adapter and connection contract](../advantest-r624x-sequence-wait-mode/overview.md)

pymeasure.instruments.advantest.advantestR624X.seq_wait(*wait_mode*, *wait_value*)

Create the command string for WAIT (sequence wait).

Parameters:

- **wait_mode** (int or `SequenceWaitMode`) — Wait mode selection (1=wait time, 2=trigger input count).

- **wait_value** (*float*) — Wait duration or trigger count.

Return type:

str
