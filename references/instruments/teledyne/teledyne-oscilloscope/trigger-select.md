# pymeasure.instruments.teledyne.TeledyneOscilloscope.trigger_select

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *trigger_select

Choose the condition, as a string, that starts waveform acquisition.

Some trigger types require extra settings. Those settings are supplied as name/value pairs: the first element identifies the variable to update, and the second gives its replacement value. Pairs can appear in any order, and only changed variables need to be included.

Five parameters may be supplied. Parameters 1. 2. 3. are always required, while Parameters 4. 5. are only needed for particular combinations of earlier parameters.

1. <trig_type>:={edge, slew, glit, intv, runt, drop}

2. <source>:={c1, c2, c3, c4, line}

3. <hold_type>:=

  - {ti, off} for edge trigger.

  - {ti} for drop trigger.

  - {ps, pl, p2, p1} applies to glit/runt trigger.

  - {is, il, i2, i1} applies to slew/intv trigger.

4. <hold_value1>:= a time value including unit.

5. <hold_value2>:= a time value including unit.

Note:

- “line” is valid only when the trigger type is “edge”.

- Provide every time argument as a multiple of seconds, using scientific notation when useful.

- Permitted hold_values depend on trigger type: [80nS, 1.5S] for “edge” trigger, and [2nS, 4.2S] for others.

- trigger_select automatically chooses the short, normal, or extended command form from the expected parameter count.
