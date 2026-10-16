# pymeasure.instruments.agilent.agilentB1500.CMU.set_measurement_mode

[Owning PyMeasure class, adapter and connection contract](overview.md)

set_measurement_mode(*measurement_mode*)

Configure MFCMU impedance measurement mode. (`IMP`)

Each MFCMU mode measures two parameters. The default is `MFCMUMeasurementMode.CP_G`.

Note

This command has no effect when the output format is binary data (FMT3, FMT4, FMT13, FMT14).

Parameters:

**measurement_mode** (`MFCMUMeasurementMode`) – Measurement mode.

Return type:

`None`
