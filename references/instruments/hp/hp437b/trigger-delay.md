# pymeasure.instruments.hp.HP437B.trigger_delay

[Owning PyMeasure class, adapter and connection contract](overview.md)

trigger_delay()

Trigger with delay.

Triggering with delay works like `trigger_immediate()`, but before the requested measurement the power meter waits for a settling-time delay. That interval lets the internal digital filter refresh with new values, producing valid and accurate measurement results. The command gives the internal amplifiers and filters time to settle; it does not include power sensor delay. For large power changes, the delay may still be too short for full settling. To ensure accurate readings, compare two consecutive measurements. After the measurement result is displayed and read onto the bus, the power meter returns to standby mode.
