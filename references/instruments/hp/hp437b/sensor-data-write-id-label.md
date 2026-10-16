# pymeasure.instruments.hp.HP437B.sensor_data_write_id_label

[Owning PyMeasure class, adapter and connection contract](overview.md)

sensor_data_write_id_label(*sensor_id*, *label*)

Select a specific power sensor's ID label table for modification. The sensor ID label cannot be longer than 7 characters. Example: identify Sensor Data table #2 with ID number 1234567:

```python
instr.sensor_data_id_label(2, "1234567")

```
