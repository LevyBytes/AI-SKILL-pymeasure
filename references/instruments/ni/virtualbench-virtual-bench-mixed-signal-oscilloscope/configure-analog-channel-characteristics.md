# pymeasure.instruments.ni.virtualbench.VirtualBench.MixedSignalOscilloscope.configure_analog_channel_characteristics

[Owning MixedSignalOscilloscope contract](overview.md)

configure_analog_channel_characteristics(*channel*, *input_impedance*, *bandwidth_limit*)

Set electrical characteristics for the specified channel

Parameters:

- **channel** (*str*) – Channel string

- **input_impedance** (*int** or **str*): Input Impedance choice (`'ONE_MEGA_OHM'` or `'FIFTY_OHMS'`)

- **bandwidth_limit** (*int*): Bandwidth limit value (100MHz or 20MHz)
