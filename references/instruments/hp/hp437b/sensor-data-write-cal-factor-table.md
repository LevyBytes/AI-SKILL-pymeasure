# pymeasure.instruments.hp.HP437B.sensor_data_write_cal_factor_table

[Owning PyMeasure class, adapter and connection contract](overview.md)

sensor_data_write_cal_factor_table(*sensor_id*, *frequency_table*, *cal_fac_table*)

Write `calibration_table` for `sensor_id` into the Sensor Data table, and write the reference calibration factor for `sensor_id`. Frequency is supplied in Hz. Calibration factor is supplied as percentage.

The power meter memory provides room for 10 tables, numbered 0-9. Tables 0-7 can hold 40 frequency/calibration factor pairs each. Tables 8 and 9 can hold 80 frequency/calibration factor pairs each.

This function clears the sensor table before it writes.

Example table:

```python
calibration_table = {
    10e6: 100.0,
    1e9: 96.5,
    2e9: 97.0
}

instr.sensor_data_cal_factor_table(0, calibration_table.keys(),
calibration_table.values())

```
