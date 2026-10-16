# pymeasure.instruments.lecroy.LeCroyT3DSO1204.trigger_mode

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *trigger_mode*: Any*

Set the trigger sweep mode (string).

&lt;mode&gt;:= {AUTO,NORM,SINGLE,STOP}

- auto : In AUTO sweep mode, the oscilloscope searches for a trigger signal satisfying the conditions. When the trigger condition is met, the upper-left running state shows Trig'd and a stable waveform appears. If not, the running state remains Auto and the waveform shown is unstable.

- normal : In NORMAL sweep mode, the oscilloscope waits for triggering while searching for trigger signals that satisfy the conditions. If the condition is met, the running state reads Trig'd and the display shows a stable waveform. Otherwise, the running state reads Ready, and the display either keeps the last triggered waveform (previous trigger) or shows no waveform (no previous trigger).

- single : In SINGLE sweep mode, the SINGLE key backlight turns on; the oscilloscope waits for a trigger and searches for a trigger signal satisfying the conditions. When the condition is met, the running state reads Trig'd and the display shows a stable waveform. The oscilloscope then halts the scan, lights the RUN/STOP key red, and reports Stop as the running status. If no trigger is found, the running state reads Ready and no waveform is displayed.

- stopped : STOP is accepted as an option for this command, but it is not an oscilloscope trigger mode.

## Related property contracts

- Open when checking pymeasure.instruments.lecroy.LeCroyT3DSO1204.trigger_select: [trigger_select](trigger-select.md).
