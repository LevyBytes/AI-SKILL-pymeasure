# pymeasure.instruments.hp.HP8116A.ask

[Owning PyMeasure class, adapter and connection contract](overview.md)

ask(*command*, *num_bytes=None*)

Sends a command to the instrument, reads the reply, and returns that reply as ASCII text.

Parameters:

- **command**: Command sent to the instrument.

- **num_bytes**: Number of bytes to read from the instrument. When omitted, the command determines the byte count automatically. (default: `None`)
