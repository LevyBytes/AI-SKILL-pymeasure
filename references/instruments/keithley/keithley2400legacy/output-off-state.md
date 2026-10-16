# pymeasure.instruments.keithley.Keithley2400Legacy.output_off_state

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *output_off_state*: Any*

Control the SourceMeter output-off state. HIMP: opens the output relay and disconnects external circuitry. NORM: selects V-Source and sets it to 0V; Compliance becomes 0.5% full scale of the present current range. ZERO: selects V-Source and sets it to 0V; compliance uses the larger of the programmed Source I value or 0.5% full scale of the present current range. GUAR: selects I-Source and sets it to 0A
