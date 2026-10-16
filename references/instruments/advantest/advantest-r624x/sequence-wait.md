# pymeasure.instruments.advantest.advantestR624X.AdvantestR624X.sequence_wait

[Owning PyMeasure class, adapter and connection contract](overview.md)

sequence_wait(*wait_mode*, *wait_value*)

Wait during sequence program execution (`WAIT`).

Parameters:

- **wait_mode** (int or `SequenceWaitMode`) – Selects whether wait time (1) or trigger input count (2) is used.

- **wait_value** (*float*) – Wait time or trigger input count, interpreted according to wait_mode.

This command provides these functions:
- Delay execution of the following program for the requested time.

- Delay the following program execution until the requested trigger count has arrived.

For either wait mode, wait data 0 disables waiting. When wait mode is “2”, these commands and signals are valid trigger inputs:
- XE (XE 0, XE 1, XE 2)

- *TRG

- GET command (group execute trigger)

- Rear-panel trigger input signal
