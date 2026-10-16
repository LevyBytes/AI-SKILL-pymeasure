# pymeasure.instruments.anritsu.AnritsuMS464xB

*class *pymeasure.instruments.anritsu.AnritsuMS464xB(*adapter*, *name='Anritsu MS464xB Vector Network Analyzer'*, *active_channels=16*, *installed_ports=4*, *traces_per_channel=None*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Class for the Anritsu MS464xB Vector Network Analyzer (VNA) series.

The family contains MS4642B, MS4644B, MS4645B, and MS4647B; their corresponding classes (`AnritsuMS4642B`, `AnritsuMS4644B`, `AnritsuMS4645B`, `AnritsuMS4647B`) vary only by available frequency range.

Depending on instrument configuration, the object can expose as many as 16 `MeasurementChannel` instances through the channels dict or directly as ch_ + the channel number.

Parameters:

- **active_channels** (*int** (**1-16**) or **str** (**"auto"**)*) - sets how many channels are active (default=16); when active_channels is "auto", the instrument is queried for the active-channel count. (default: `16`)

- **installed_ports** (*int** (**1-4**) or **str** (**"auto"**)*) - sets how many ports are installed (default=4); with "auto", the instrument is queried for the port count. (default: `4`)

- **traces_per_channel** (*int** (**1-16**) or **str** (**"auto"**) or **None*) - sets the assumed traces per channel (between 1 and 16); when omitted, the maximum is assumed; with "auto", the instrument is queried for each channel's trace count. (default: `None`)
