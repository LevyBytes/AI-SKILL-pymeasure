# pymeasure.instruments.advantest.advantestR624X.AdvantestR624X.status_byte_register

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *status_byte_register*: Any*

Read the status byte register and MSS bits without performing a serial poll (`*STB?`).

The Status Byte Register is hierarchical. Except for RQS and MAV, the ERR, DOP, ESB, and COP bits have subordinate status registers. Each status register has a corresponding enable register that determines whether it can output to the Status Byte register. The status byte register also has an enable register, which selects whether a service request SRQ is issued.

Note

`*STB?` can read bit 6 as MSS (logical OR of other bits).
