# Fixed Level Sweep Program Example

Measurement characteristics:

Function: VSVM - Voltage source and voltage measurement.
Level value: 15V. Bias value: 0V. Number of measurements: 20 times.
Compliance: 6mA. Measuring range: Best fixed range (=60V range).
Integration time: 100us. Measurement delay time: 0. Hold time: 1ms.
Sampling mode: automatic sweep.
Measurement data output method: Buffering output (output of specified data).

After operation starts, make 20 measurements in fixed sweep. Detect sweep completion by checking the Channel Operation Register (COR). After the sweep is finished, read measured data from 1 to 2 using the RMM command.

The complete program is in the [upstream source](https://raw.githubusercontent.com/pymeasure/pymeasure/08c4a91f5255c937a909cc21e70fa3fafd76333e/pymeasure/instruments/advantest/advantestR624X.py).
