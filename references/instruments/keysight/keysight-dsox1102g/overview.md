# pymeasure.instruments.keysight.KeysightDSOX1102G

Covers: Keysight DSOX1102G Oscilloscope; Keysight PNA Vector Network Analyzers.

## Keysight DSOX1102G Oscilloscope

### Keysight DSOX1102G Oscilloscope

 *class *pymeasure.instruments.keysight.KeysightDSOX1102G(*adapter*, *name='Keysight DSOX1102G Oscilloscope'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Interface for the Keysight DSOX1102G Oscilloscope used to communicate with and control the instrument.

For direct scope control through the lower-level methods, consult the Keysight DSOX1102G Oscilloscope Programmer’s Guide.

```python
from pymeasure.instruments.keysight.keysightDSOX1102G import KeysightDSOX1102G

scope = KeysightDSOX1102G(resource)
scope.autoscale()
ch1_data_array, ch1_preamble = scope.download_data(source="channel1", points=2000)
# ...
scope.shutdown()

```

Known issues:

- Completion reporting can occur before digitize itself has finished. Commands sent immediately after digitize may produce VI_ERROR_TMO (timeout). Current fix: when necessary, wait between digitize and the next command sent to the scope.
