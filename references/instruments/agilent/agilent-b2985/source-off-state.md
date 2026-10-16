# pymeasure.instruments.agilent.AgilentB2985.source_off_state

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *source_off_state*: Any*

Configure the voltage source off condition.

Type:

str; accepted values are exactly `ZERO`, `HIZ`, `NORM`

| `HIGH Z` | - Output relay: off (open) - The voltage source setting remains unchanged. - This status is available only with the 20 V range. |
| --- | --- |
| `NORMAL` | - Output voltage: 0 V - Output relay: off (open) |
| `ZERO` | - Output voltage: 0 V in the active voltage range |
