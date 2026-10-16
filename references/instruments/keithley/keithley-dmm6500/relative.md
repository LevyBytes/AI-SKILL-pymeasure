# pymeasure.instruments.keithley.KeithleyDMM6500.relative

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *relative*: Any*

Set the relative offset value for the currently active `mode`. When relative offset is enabled, later readings are shifted by the value configured with this command. If the instrument captures the value internally, reading this setting returns that measured value. See also the `relative_enabled`.
