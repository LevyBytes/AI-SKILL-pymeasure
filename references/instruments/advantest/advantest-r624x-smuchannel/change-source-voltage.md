# pymeasure.instruments.advantest.advantestR624X.SMUChannel.change_source_voltage

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *change_source_voltage*: Any*

Set new target voltage (`SPOT`).

Type:

float

Note

This changes only the DC action source value and the pulse action pulse value, reusing the DC action and pulse action parameters already configured. After changing them, measure and assign the channel whose measured data should be output to the specified ch. It is equivalent to these commands:
1. DV/DI/PV/PI

2. XE xx

3. FCH xx
