# pymeasure.instruments.teledyne.TeledyneMAUI.trigger

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *trigger

Return trigger configuration as a dict containing these keys:

- “mode”: trigger sweep mode [auto, normal, single, stop]

- “trigger_type”: waveform acquisition trigger condition [edge,slew,glit,intv,runt,drop]

- “source”: trigger source [c1,c2,c3,c4]

- “hold_type”: hold type (refer to page 172 of programing guide)

- “hold_value1”: hold value1 (refer to page 172 of programing guide)

- “hold_value2”: hold value2 (refer to page 172 of programing guide)

- “coupling”: coupling applied to the chosen trigger sources

- “level”: active trigger source voltage level

- “slope”: slope setting for the selected trigger source
