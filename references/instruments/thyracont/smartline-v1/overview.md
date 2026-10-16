# pymeasure.instruments.thyracont.smartline_v1.SmartlineV1

*class *pymeasure.instruments.thyracont.smartline_v1.SmartlineV1(*adapter*, *name='Thyracont Vacuum Gauge V1'*, *address=1*, *baud_rate=9600*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Thyracont Vacuum Instruments Smartline gauges that use Communication Protocol V1.

Protocol V1 applies to devices manufactured until 2017.

The device connection uses RS485 serial communication. By default it communicates at baudrate 9600 with 8 data bits, 1 stop bit, no parity, and no handshake.

A communication package is organized as follows:

Characters 0-2: Communication address Character 3: Command character; uppercase letters read and lowercase letters write Characters 4-n: Command data, possibly empty. Character n+1: Checksum; sum decimal values for bytes 0-n, then use mod 64 + 64 Character n+2: Carriage return

Parameters:

- **adapter** – pyvisa resource name for the instrument, or an adapter instance

- **name** (*string*) – Instrument name.

- **address** (*int*) – RS485 adddress for the instrument, 1-15.

- **baud_rate** (*int*) – baudrate used when communicating with the device.

- **kwargs** – Any key-word argument accepted by Instrument
