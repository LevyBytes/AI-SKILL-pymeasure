# pymeasure.instruments.keithley.Keithley2450.voltage_output_off_state

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *voltage_output_off_state*: Any*

Set or read SourceMeter output behavior. HIMP : output relay is open and disconnects external circuitry. NORM : select V-Source, set it to 0V, and set Compliance to 0.5% full scale of the present current range. ZERO : select V-Source, set it to 0V, and set compliance to whichever is greater: the programmed Source I value or 0.5% full scale of the present current range. GUAR : select I-Source and set it to 0A
