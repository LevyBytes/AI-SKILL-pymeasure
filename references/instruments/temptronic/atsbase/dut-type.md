# pymeasure.instruments.temptronic.ATSBase.dut_type

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *dut_type*: Any*

Control DUT sensor type.

Type:

string

Possible values are:

| String | Meaning |
| --- | --- |
| ‘’ | no DUT |
| ‘T’ | T-DUT |
| ‘K’ | K-DUT |

Warning: Running in DUT mode without a connected DUT makes TS flag a DUT error
