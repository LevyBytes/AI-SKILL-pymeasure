# pymeasure.instruments.hp.HP3478A.write_calibration_data

[Owning PyMeasure class, adapter and connection contract](overview.md)

write_calibration_data(*cal_data*, *verify_calibration_data=True*)

Method to write calibration data.

The cal_data parameter uses the same format as the `calibration_data` property.

Set `verify_calibration_data` to `False` to skip verification of the cal_data array.
