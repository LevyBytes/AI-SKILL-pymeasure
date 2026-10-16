# pymeasure.instruments.advantest.advantestR624X.CurrentRange

*class *pymeasure.instruments.advantest.advantestR624X.CurrentRange(**values*)

Bases: `IntEnum`

Current measurement/source range selection.

Warning

`AUTO` and `AUTO_*` (limited auto) ranges are invalid for pulse measurement or pulse sweep. In pulsed modes they trigger error 00211 (“command cannot be executed in current settings”); choose a fixed range such as `FIXED_BEST` instead.

With integration time in sample hold mode (SH) from 100 μs through 500 μs, resolution drops: 10 digits at 100 μs, 5 at 200 μs, and 2 at 500 μs.
