# pymeasure.instruments.keithley.Keithley6221.define_arbitary_waveform

[Owning PyMeasure class, adapter and connection contract](overview.md)

define_arbitary_waveform(*datapoints*, *location=1*)

Define arbitrary waveform data points, then copy that waveform definition to the specified storage location.

Parameters:

- **datapoints** – list (or numpy array) of data points; every value must be between -1 and 1; 100 points maximum.

- **location** – integer storage location where the waveform is stored. Value must be in range 1 to 4. (default: `1`)
