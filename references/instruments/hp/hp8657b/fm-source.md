# pymeasure.instruments.hp.HP8657B.fm_source

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *fm_source*: Any*

Selects the FM function source using the `Modulation` enumeration.

| Value | Meaning |
| --- | --- |
| OFF | no modulation active |
| INT_400HZ | internal 400 Hz modulation source |
| INT_1000HZ | internal 1000 Hz modulation source |
| EXTERNAL | External source, AC coupling |
| DC_FM | External source with DC coupling (FM only) |

*Note:*

- AM & FM may both be active at the same time.

- Only a single internal source can be active at one time.

- use “OFF” to deactivate FM

- Refer to the documentation for details on use of DC FM mode.

usage example:

```python
from pymeasure.instruments.hp.hp8657b import HP8657B

sig_gen = HP8657B("GPIB::7")
...
sig_gen.fm_source = sig_gen.Modulation.EXTERNAL     #  Enable external source for FM
sig_gen.fm_deviation = 15                           #  Set FM peak deviation to 15 kHz
...
sig_gen.fm_source = sig_gen.Modulation.OFF          #  Turn FM off

```
