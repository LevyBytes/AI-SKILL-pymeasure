# pymeasure.instruments.keithley.keithley2182.Keithley2182Channel

*class *pymeasure.instruments.keithley.keithley2182.Keithley2182Channel(*parent*, *id*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Implementation of a Keithley 2182 channel.

Channel 1 is the primary measurement channel; channel 2 supplies sense measurements. Channel 2 inputs reference Channel 1 LO. Possible configurations are

Supported configurations: Voltage (Channel 1); Temperature (Channel 1); dual voltage using Voltage (Channel 1) and Voltage (Channel 2); voltage plus temperature using Voltage (Channel 1) and Temperature (Channel 2)
