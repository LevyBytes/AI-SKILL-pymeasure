# pymeasure.instruments.rohdeschwarz.sfm.SFM.serial_flowcontrol

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *serial_flowcontrol*: Any*

String property selecting the handshake type used for serial communication.

Possible values are:

| Value | Meaning |
| --- | --- |
| NONE | no flow-control/handshake |
| XON | XON/XOFF flow-control |
| ACK | hardware handshake with RTS&CTS |
