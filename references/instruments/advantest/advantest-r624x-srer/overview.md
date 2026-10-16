# pymeasure.instruments.advantest.advantestR624X.SRER

*class *pymeasure.instruments.advantest.advantestR624X.SRER(**values*)

Bases: `IntFlag`

Service Request Enable Register (SRER) bit assigment:

| Bit (dec) | Description |
| --- | --- |
| 0 | none |
| 1 | ERR is set when any SESR flag QYE, DDE, EXE, or CME is set in the Standard Event Status Register (SESR). |
| 2 | DOP is set when an enabled bit in the device operation register becomes set. Reading the device operation register clears DOP. |
| 3 | none |
| 4 | MAV is set after output data enters the output queue. Reading the output data clears MAV. |
| 5 | ESB is set when an enabled bit in the Standard Event Status Register (SESR) is set. Reading SESR clears ESB. |
| 6 | RQS (MSS) is set when bit O through bit 5 and bit 7 are set in the Status Byte register. (this bit is read-only) |
| 7 | COP is set when an enabled bit in the Channel Operations Register becomes set. Reading the Channel Operations Register clears COP. |
