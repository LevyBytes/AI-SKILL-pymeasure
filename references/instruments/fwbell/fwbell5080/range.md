# pymeasure.instruments.fwbell.FWBell5080.range

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *range*: Any*

Set or read the maximum field range in the active units (int). The current units mode controls the range unit (gauss, tesla, amp-meter). The value selects an equivalent range across units with increasing magnitude (1, 10, 100).

| Value | gauss | tesla | amp-meter |
| --- | --- | --- | --- |
| 0 | 300 G | 30 mT | 23.88 kAm |
| 1 | 3 kG | 300 mT | 238.8 kAm |
| 2 | 30 kG | 3 T | 2388 kAm |
