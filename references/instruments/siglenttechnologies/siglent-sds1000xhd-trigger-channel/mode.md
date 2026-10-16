# pymeasure.instruments.siglenttechnologies.siglent_sds1000xhd.TriggerChannel.mode

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *mode*: Any*

Control the trigger mode.

Available options:

- AUTO: the oscilloscope searches for a trigger signal. If the condition is met, it displays ‘Trig’d’ with a stable waveform. Otherwise, it displays ‘Auto’ and an unstable waveform.

- NORMal: the oscilloscope waits for a trigger signal. If the condition is met, it displays ‘Trig’d’ with a stable waveform. Otherwise, it displays ‘Ready’ and the last triggered waveform.

- SINGle: single trigger mode. The oscilloscope waits for a trigger, then stops scanning once the trigger condition is satisfied.

- FTRIG: force a trigger so a frame is acquired regardless of trigger conditions.
