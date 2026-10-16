# pymeasure.instruments.advantest.advantestR624X.AdvantestR624X.trigger_output_signal

[Owning PyMeasure class, adapter and connection contract](overview.md)

trigger_output_signal(*trigger_output*, *alarm_output*, *scanner_output*)

Emit trigger, alarm, and scanner (start/stop) signals from GPIB (`OSIG`).

Parameters:

- **trigger_output** (*int*) – Number selecting the trigger output type

- **alarm_output** (*int*) – Number selecting the alarm output type

- **scanner_output** (*int*) – Number selecting the scanner output type

Trigger output:

1. Send nothing to the trigger output.

2. Send a negative pulse to the trigger output.

Alarm output:

1. Finish output with GO and LO.HI both at HI level. (reset)

2. Finish output by setting GO to LO level.

3. Drive home output LO to LO level.

4. End output by moving HI to LO level.

Scanner - (start/stop) output:

1. Drive the scanner scoot output to HI level. Send a negative pulse to the stop output.

2. Set the scanner start output low.

3. Send HI level on the scanner start output and a negative pulse on the stop output.
