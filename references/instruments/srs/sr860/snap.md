# pymeasure.instruments.srs.SR860.snap

[Owning PyMeasure class, adapter and connection contract](overview.md)

snap(*val1='X'*, *val2='Y'*, *val3=None*)

Retrieves 2 or 3 parameters together; parameters may be selected by index or enumeration as follows:

| index | enumeration | parameter |
| --- | --- | --- |
| 0 | X | X output |
| 1 | Y | Y output |
| 2 | R | R output |
| 3 | THeta | θ output |
| 4 | IN1 | Aux In1 |
| 5 | IN2 | Aux In2 |
| 6 | IN3 | Aux In3 |
| 7 | IN4 | Aux In4 |
| 8 | XNOise | Xnoise |
| 9 | YNOise | Ynoise |
| 10 | OUT1 | Aux Out1 |
| 11 | OUT2 | Aux Out2 |
| 12 | PHAse | Reference Phase |
| 13 | SAMp | Sine Out Amplitude |
| 14 | LEVel | DC Level |
| 15 | FInt | Int. Ref. Frequency |
| 16 | FExt | Ext. Ref. Frequency |

Parameters:

- **val1** – parameter enumeration/index (default: `'X'`)

- **val2** – parameter enumeration/index (default: `'Y'`)

- **val3** – parameter enumeration/index (optional) (default: `None`)

Defaults:

val1 = “X” val2 = “Y” val3 = None
