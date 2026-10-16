# pymeasure.instruments.hp.hp856Xx.HP856Xx.marker_threshold

HP856Xx.marker_threshold

Set the minimum amplitude level that can qualify a trace peak for detection. The default setting is -130 dBm. The related `peak_excursion` command defines the excursion requirement. Peak excursion evaluation can include the part of a peak that falls below the threshold. For example, with peak excursion set to 6 dB, a peak that is 3 dB above the threshold is found if it extends at least another 3 dB below the threshold. Maximum 30 db to minimum -200 db.

Type: `signed int`

```python
instr.marker_threshold = -70
if instr.marker_threshold > -80:
    pass

```
