# pymeasure.instruments.lecroy.LeCroyT3DSO1204.trigger

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *trigger

Return trigger setup as a dict using these keys:

- “mode”: trigger sweep mode [auto, normal, single, stop]

- `trigger_type`: waveform-acquisition trigger condition [edge, slew,glit,intv,runt,drop]

- “source”: trigger source [c1,c2,c3,c4]

- `hold_type`: hold type; see page 172 of programing guide

- `hold_value1`: hold value1; see page 172 of programing guide

- `hold_value2`: hold value2; see page 172 of programing guide

- `coupling`: input coupling for the selected trigger sources

- `level`: trigger-level voltage for the active trigger source

- `level2`: lower trigger-level voltage for the active trigger source (only slew/runt trigger)

- `slope`: specified trigger source trigger slope
