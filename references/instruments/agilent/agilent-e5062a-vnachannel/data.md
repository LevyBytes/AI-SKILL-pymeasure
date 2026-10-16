# pymeasure.instruments.agilent.agilentE5062A.VNAChannel.data

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *data

Read Formatted Data for the *active trace*.

A trace contains `scan_points` samples plotted either against frequency or in a Smith-chart-style arrangement. This property does not return frequency values. For rectangular plots, the query therefore returns just trace y-values. For smith- and polar- plots, it returns two values per data point.

Returns a tuple with primary and secondary data numpy arrays. For trace formats other than smith or polar, secondary data contains only zeros. To capture complex S-parameter data in one operation, use a Smith (Real/Imag) or Polar (Real/Imag) trace format, respectively SCOMplex or POLar.

The VNA can accept formatted data arrays, but this python API does not implement setting them.

Read frequency data from the `frequencies` property.

```python
# build an s-parameter matrix by measuring the trace data,
# where s_matrix[i] = [[S11, S12], [S21, S22]] @ freqs[i]
freqs = ch.frequencies
s_matrix = np.empty((freqs.size, 4), dtype=np.complex64)
for i, tr in enumerate(ch.traces.values()):
    tr.activate()
    ch.trace_format = 'POL'
    re, im = ch.data
    s_matrix[:, i] = re + 1j * im
s_matrix = s_matrix.reshape(-1, 2, 2)  # ready for use with e.g. skrf

```
