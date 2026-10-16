# pymeasure.instruments.thyracont.smartline_v2.SmartlineV2.ask

[Owning PyMeasure class, adapter and connection contract](overview.md)

ask(*command_message*, *query_delay=None*)

Request a value, then verify that the reply corresponds to the command originally sent.

Parameters:

**command_message** (*str*) – Access code, command, length, and content; the transmitted command is checked against the response command.
