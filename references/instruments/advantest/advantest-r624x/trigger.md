# pymeasure.instruments.advantest.advantestR624X.AdvantestR624X.trigger

[Owning PyMeasure class, adapter and connection contract](overview.md)

trigger()

Use `XE` to issue the trigger signal, or to start sweep/search measurement across the A channel, B channel, and trigger link.

Note

- If A channel and B channel are both waiting for a trigger, the trigger is applied to both.

- If only one of channel A or B is waiting for a trigger, that waiting channel alone is triggered.

- If A channel and B channel are both waiting for sweep start, sweep start is applied to both.

- If only one of channel A or B is in the sweep start waiting state, start only that channel.

- If one channel is waiting for a trigger and the other for sweep start, apply the trigger and sweep start to their respective channels.

- With trigger link ON on the master unit, drive the *TRG signal on the trigger link bus TRUE.

- When trigger link is ON and the unit is the master, activate the trigger link.
