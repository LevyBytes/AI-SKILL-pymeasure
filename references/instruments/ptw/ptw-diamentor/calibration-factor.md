# pymeasure.instruments.ptw.ptwDIAMENTOR.calibration_factor

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *calibration_factor*: Any*

Set the measurement chamber calibration factor in µGy*mÂ²/s (float, strictly from `1E8` to `9.999E12`, default: `1.0E9`).

The calibration factor unit is always µGy*mÂ²/s and does not depend on the selected `dap_unit`.

Warning

Changing the calibration factor can produce incorrect measurements!

Find the last calibration factor on the case label or in the DIAMENTOR chamber calibration certificate.
