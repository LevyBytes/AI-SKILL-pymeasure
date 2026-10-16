# pymeasure.instruments.hp.hp856Xx.HP856Xx.threshold

HP856Xx.threshold

Set the lower amplitude limit and clip data at that level. The default value is -90 dBm. See also - `marker_threshold`, which leaves data below its threshold intact.

Type: `str, float` range -200 to 30

Note

In max-hold mode, raising the threshold above existing trace points permanently removes the trace data below that threshold.
