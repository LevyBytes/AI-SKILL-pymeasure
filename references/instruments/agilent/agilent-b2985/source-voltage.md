# pymeasure.instruments.agilent.AgilentB2985.source_voltage

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *source_voltage*: Any*

Configure the source voltage in Volts.

Type:

float, strictly from `-1050` to `1050`

For voltages > 20V, the interlock must be closed.

| Range | Resolution | Output voltage | Maximum current |
| --- | --- | --- | --- |
| 20 V | 700 µV | -21 V ≤ V ≤ 21 V | +/-20 mA |
| 1000 V | 35 mV | -1 V ≤ V ≤ 1000 V | +/-1.0 mA |
| -1000 V | 35 mV | -1000 V ≤ V ≤ 1 V | +/-1.0 mA |
