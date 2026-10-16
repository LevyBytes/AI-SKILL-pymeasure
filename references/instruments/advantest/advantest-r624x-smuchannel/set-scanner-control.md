# pymeasure.instruments.advantest.advantestR624X.SMUChannel.set_scanner_control

[Owning PyMeasure class, adapter and connection contract](overview.md)

set_scanner_control(*output*, *interlock*)

Configure the rear-panel SCANNER CONTROL (START, STOP) output signal and INTERLOCK input signal (`SCT`).

Parameters:

- **output** (*int*) – Property controlling the scanner output

- **interlock** (*int*) – Property controlling the scanner interlock type

output:
1. Scanner, turn off the control signal output.

2. Output the scanner control signal at sweep start / stop.

3. Operate / Standby Scanner, output to the control signal.

interlock:
1. Disable the interlock signal input.

2. Use stamper behavior when the interlock signal input is HI.

3. When the interlock signal input is HI, standby is selected; when it is LO, operation is selected.
