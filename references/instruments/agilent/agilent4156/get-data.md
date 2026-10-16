# pymeasure.instruments.agilent.agilent4156.Agilent4156.get_data

[Owning PyMeasure class, adapter and connection contract](overview.md)

get_data(*path=None*)

Retrieve measurement data from the instrument once the run is complete.

When `measure()` uses measurement period `INF`, call `stop()` before retrieving data; otherwise valid data is not available.

Parameters:

**path** — Optional CSV export path. (default: `None`)

Returns:

Pandas Dataframe

```python
df = instr.get_data(path='./datafolder/data1.csv')

```
