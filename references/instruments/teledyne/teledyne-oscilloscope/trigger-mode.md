# pymeasure.instruments.teledyne.TeledyneOscilloscope.trigger_mode

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *trigger_mode*: Any*

Set the trigger sweep mode using a string value.

&lt;mode&gt;:= {AUTO,NORM,SINGLE,STOP}

- auto : In AUTO sweep mode, the oscilloscope searches for a signal matching the trigger conditions. When the condition is met, the upper-left running state displays Trig’d and a stable waveform is shown. If it is not met, the state remains Auto and the displayed waveform is unstable.

- normal : In NORMAL sweep mode, the oscilloscope waits for a trigger and searches for signals satisfying the configured conditions. A successful trigger makes the running state display Trig’d and shows a stable waveform. Without a matching trigger, the state displays Ready and the screen either keeps the previous triggered waveform or, if none exists, shows no waveform.

- single : In SINGLE sweep mode, the SINGLE key backlight turns on and the oscilloscope waits while checking for a trigger signal that satisfies the conditions. On a match, the running state shows Trig’d and the waveform becomes stable. The oscilloscope then stops scanning, the RUN/STOP key lights red, and the status changes to Stop. If no trigger is found, the state shows Ready and no waveform is displayed.

- stopped : STOP is accepted by this command as an option, although it is not an oscilloscope trigger mode.

## Related property contracts

- Open when checking pymeasure.instruments.teledyne.TeledyneOscilloscope.trigger_select: [trigger_select](trigger-select.md).
