# pymeasure.instruments.keithley.Keithley2450.current_output_off_state

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *current_output_off_state*: Any*

Set or read SourceMeter output behavior. HIMP : opens the output relay, disconnecting external circuitry. NORM : selects V-Source, sets it to 0V, and sets Compliance to 0.5% full scale of the present current range. ZERO : selects V-Source, sets it to 0V, and sets compliance to whichever is greater: the programmed Source I value or 0.5% full scale of the present current range. GUAR : selects I-Source and sets it to 0A
