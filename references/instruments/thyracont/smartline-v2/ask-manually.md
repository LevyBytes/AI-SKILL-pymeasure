# pymeasure.instruments.thyracont.smartline_v2.SmartlineV2.ask_manually

[Owning PyMeasure class, adapter and connection contract](overview.md)

ask_manually(*accessCode*, *command*, *data=''*, *query_delay=None*)

Transmit a message to the transmitter and return the reply.

Parameters:

- **accessCode** – Access method for the device.

- **command** – Command that will be sent to the device.

- **data** – Command data. (default: `''`)

- **query_delay** (*float*) – Seconds to pause after writing before reading.

Return str:

Device response after error checks have completed.
