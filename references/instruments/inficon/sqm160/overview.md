# pymeasure.instruments.inficon.sqm160.SQM160

*class *pymeasure.instruments.inficon.sqm160.SQM160(*adapter*, *name='Inficon SQM-160 thickness monitor'*, *baud_rate=19200*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Inficon SQM-160 multi-film rate/thickness monitor.

Uses a quartz crystal sensor to measure rate and thickness during thin film deposition. Device connection is typically through serial (RS232), with USB or Ethernet as optional alternatives.

Each command packet always contains:

- 1 Byte: Sync character; '!' occurs only at message start.

- 1 Byte: length character derived from message length without CRC.

34 is added to prevent any '!' from appearing.

- Command message with variable length.

- 2 Byte: Cyclic Redundancy Check (CRC) checksum.

Each response packet always contains:

- 1 Byte: Sync character; '!' occurs only at message start.

- 1 Byte: length character derived from message length without CRC.

A value of 35 is added.

- 1 Byte: response status character that reports command status.

- Response message with variable length.

- 2 Byte: Cyclic Redundancy Check (CRC) checksum.

Parameters:

- **adapter** - pyvisa resource name for the instrument, or an adapter instance

- **name** (*string*) - Instrument name.

- **baud_rate** (*string*) - Serial connection baud rate.

- **kwargs** - Any valid key-word argument for Instrument
