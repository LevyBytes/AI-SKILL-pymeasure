# pymeasure.instruments.lecroy.LeCroyT3DSO1204.measure_delay

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *measure_delay*: Any*

Control measurement delay.

MEASURE_DELY puts the instrument into continuous measurement mode and begins a selected delay measurement. The MEASURE_DELY? query returns the measured delay value. The command takes three arguments using this syntax:
measure_delay = (&lt;type&gt;,&lt;sourceA&gt;,&lt;sourceB&gt;)

&lt;type&gt; := {PHA,FRR,FRF,FFR,FFF,LRR,LRF,LFR,LFF,SKEW}

Valid pair form: &lt;sourceA&gt;,&lt;sourceB&gt; := {C1,C2,C3,C4}; when sourceA=CX and sourceB=CY, require X < Y.

| Type | Description |
| --- | --- |
| PHA | Phase difference for two channels. (rising edge - rising edge) |
| FRR | Two-channel delay. (first rising edge - first rising edge) |
| FRF | Two-channel delay. (first rising edge - first falling edge) |
| FFR | Two-channel delay. (first falling edge - first rising edge) |
| FFF | Two-channel delay. (first falling edge - first falling edge) |
| LRR | Two-channel delay. (first rising edge - last rising edge) |
| LRF | Two-channel delay. (first rising edge - last falling edge) |
| LFR | Two-channel delay. (first falling edge - last rising edge) |
| LFF | Two-channel delay. (first falling edge - last falling edge) |
| Skew | Two-channel delay. (edge – edge of the same type) |
