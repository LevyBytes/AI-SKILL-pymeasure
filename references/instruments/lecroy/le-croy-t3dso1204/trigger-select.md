# pymeasure.instruments.lecroy.LeCroyT3DSO1204.trigger_select

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *trigger_select

Set the waveform-acquisition trigger condition (string).

Some trigger types require additional parameters. Supply those extra parameters as pairs: the first element names the variable to change, and the second provides its new value. The pairs can appear in any order and can be limited to only the variables being changed.

Five parameters can be specified. Parameters 1. 2. 3. are required in every case. Parameters 4. 5. are only needed for particular combinations of the earlier parameters.

1. <trig_type>:={edge, slew, glit, intv, runt, drop}

2. <source>:={c1, c2, c3, c4, line}

3. <hold_type>:=

  - {ti, off} for edge trigger.

  - {ti} for drop trigger.

  - {ps, pl, p2, p1} applies to glit/runt trigger.

  - {is, il, i2, i1} applies to slew/intv trigger.

4. <hold_value1>:= a time value with unit.

5. <hold_value2>:= a time value with unit.

Note:

- `line` is selectable only with trigger type `edge`.

- Give all time arguments as multiples of seconds; use scientific notation when needed.

- hold_values ranges depend on trigger type: [80nS, 1.5S] for `edge` trigger, and [2nS, 4.2S] for the others.

- `trigger_select` switches automatically among the short, normal, and extended versions according to the expected parameter count.
