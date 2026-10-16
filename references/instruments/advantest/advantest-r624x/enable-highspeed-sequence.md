# pymeasure.instruments.advantest.advantestR624X.AdvantestR624X.enable_highspeed_sequence

[Owning PyMeasure class, adapter and connection contract](overview.md)

enable_highspeed_sequence(*trigger_mode*)

Permit a high-speed sequence program to start (`PGON`).

Parameters:

**trigger_mode** (int or `HighSpeedTriggerMode`) – Trigger mode used for program execution.

Trigger modes:

1. Continuous: runs all programs sequentially after one trigger.

2. Step: runs one program for each trigger.

3. Execution trigger measurement: applies settings first, then waits for a trigger before each measurement.

Note

Before calling this method, store programs in program numbers 1-20 with `store_highspeed_sequence()`. Program numbers with no stored program are skipped.
