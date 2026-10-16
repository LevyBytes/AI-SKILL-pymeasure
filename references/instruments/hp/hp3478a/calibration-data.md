# pymeasure.instruments.hp.HP3478A.calibration_data

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *calibration_data

Read and update calibration data as a 256-value array containing values from 0 through 15.

The HP 3478A calibration data resides in 256x4 SRAM kept alive by a 3v Lithium battery; if that battery is depleted, the data is erased and the instrument must be recalibrated.

On read, the property retrieves calibration data and returns it for backup use.

On assignment, provide an array of 256 values from 0 to 15; those values are written to the instrument.

Write operations raise exceptions in these cases:

- The front-panel CAL ENABLE switch is not ON.

- The value array has a length other than 256 elements.

- The value array fails the verification check.

IMPORTANT: editing calibration data permanently replaces the prior data. Use with care!
