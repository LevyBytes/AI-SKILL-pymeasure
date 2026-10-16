# pymeasure.instruments.rohdeschwarz.sfm.SFM.level_mode

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *level_mode*: Any*

String property selecting output attenuator behavior and linearity mode.

Possible selections are:

| Value | Meaning | max. output level |
| --- | --- | --- |
| NORM | Normal mode | +6 dBm |
| LOWN | low noise mode | +10 dBm |
| CONT | continuous mode | +10 dBm |
| LOWD | low distortion mode | +0 dBm |

Continuous mode permits as much as 14 dB of level adjustment without engaging the mechanical attenuator.
