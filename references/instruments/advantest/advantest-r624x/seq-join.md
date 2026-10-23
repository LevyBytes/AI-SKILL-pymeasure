# pymeasure.instruments.advantest.advantestR624X.seq_join

[Owning PyMeasure class, adapter and connection contract](../advantest-r624x-sequence-wait-mode/overview.md)

pymeasure.instruments.advantest.advantestR624X.seq_join(**commands*)

Combine multiple sequence command strings using semicolons.

Parameters:

**commands**: One or more command strings returned by `seq_*` functions.

Return type:

str

Example:

```python
from pymeasure.instruments.advantest.advantestR624X import VoltageRange

cmd = seq_join(
    seq_voltage_source(1, VoltageRange.FIXED_BEST, 5.0, 0.1),
    seq_enable_source(1),
)
inst.store_highspeed_sequence(1, cmd)

```
