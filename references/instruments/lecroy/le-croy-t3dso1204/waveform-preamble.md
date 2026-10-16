# pymeasure.instruments.lecroy.LeCroyT3DSO1204.waveform_preamble

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *waveform_preamble

Return selected-waveform-source preamble information as a dict with these keys:

- “type”: normal, peak detect, average, high resolution (str)

- `requested_points`: user-requested number of data points (int)

- `sampled_points`: data-point count sampled by the oscilloscope (int)

- `transmitted_points`: count of data points actually transmitted (optional) (int)

- `memory_size`: oscilloscope internal-memory size in bytes (int)

- `sparsing`: sparse point; it sets the interval between data points. (int)

- `first_point`: first data point address to be sent (int)

- `source`: data source: `C1`, `C2`, `C3`, `C4`, `MATH`.

- `unit`: physical units used for the Y-axis

- `type`: data acquisition type. Can be `normal`, `peak`, `average`, `highres`

- `average`: number of times used for average acquisition

- `sampling_rate`: sampling rate; this property is read-only

- `grid_number`: horizontal grid count; this property is read-only

- `status`: scope acquisition status. Can be `stopped`, `triggered`, `ready`, `auto`, `armed`

- `xdiv`: horizontal scale in seconds, using units per division

- `xoffset`: seconds between the trigger event and the reference position

- `ydiv`: vertical scale in Volts, using units per division

- `yoffset`: value shown at the screen center, in Volts
