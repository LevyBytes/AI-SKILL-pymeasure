# pymeasure.instruments.hp.HP3478A.verify_calibration_data

[Owning PyMeasure class, adapter and connection contract](overview.md)

verify_calibration_data(*cal_data*)

Checks every calibration-entry checksum.

Requires an array of 256 values containing calibration data.

Return calibration_correct:

True if every checksum is correct.

Rtype calibration_correct:

boolean
