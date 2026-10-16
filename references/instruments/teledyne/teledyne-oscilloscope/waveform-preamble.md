# pymeasure.instruments.teledyne.TeledyneOscilloscope.waveform_preamble

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *waveform_preamble

Return preamble data for the chosen waveform source as a dict with these keys:

- “requested_points”: data point count requested by the user (int)

- “sampled_points”: data point count sampled by the oscilloscope (int)

- “transmitted_points”: data point count actually transmitted, when present (int)

- “memory_size”: internal oscilloscope memory size in bytes (int)

- “sparsing”: sparse point. It gives the spacing between data points. (int)

- “first_point”: address for the first data point to transmit (int)

- “source”: data source : “C1”, “C2”, “C3”, “C4”, “MATH”.

- “grid_number”: count of horizontal grids; this property is read-only

- “xdiv”: horizontal seconds-per-division scale

- “xoffset”: seconds between the trigger event and the reference position

- “ydiv”: vertical scale, in Volts per division

- “yoffset”: Volts value displayed at screen center
