# pymeasure.instruments.hp.HP8657B.am_source

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *am_source*: Any*

Selects the AM function source using the `Modulation` enumeration.

| Value | Meaning |
| --- | --- |
| OFF | no modulation active |
| INT_400HZ | internal 400 Hz modulation source |
| INT_1000HZ | internal 1000 Hz modulation source |
| EXTERNAL | External source, AC coupling |

*Note:*

- AM & FM may both be active at the same time.

- Only a single internal source can be active at one time.

- use “OFF” to deactivate AM

usage example:

```python
from pymeasure.instruments.hp.hp8657b import HP8657B

sig_gen = HP8657B("GPIB::7")
...
sig_gen.am_source = sig_gen.Modulation.INT_400HZ    #  Enable int. 400 Hz source for AM
sig_gen.am_depth = 50                               #  Set AM modulation depth to 50%
...
sig_gen.am_source = sig_gen.Modulation.OFF          #  Turn AM off

```
