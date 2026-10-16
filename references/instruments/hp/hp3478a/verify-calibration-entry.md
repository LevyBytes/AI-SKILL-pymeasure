# pymeasure.instruments.hp.HP3478A.verify_calibration_entry

[Owning PyMeasure class, adapter and connection contract](overview.md)

verify_calibration_entry(*cal_data*, *entry_nr*)

Checks the checksum for a single calibration entry.

Requires an array of 256 calibration-data values plus an entry number from 0 to 18.

Returns True if the selected calibration entry checksum is correct.
