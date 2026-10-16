# pymeasure.instruments.lecroy.LeCroyT3DSO1204

*class *pymeasure.instruments.lecroy.LeCroyT3DSO1204(*adapter*, *name='LeCroy T3DSO1204 Oscilloscope'*, ***kwargs*)

Bases: [`TeledyneOscilloscope`](https://pymeasure.readthedocs.io/en/latest/api/instruments/teledyne/teledyne_bases.html#pymeasure.instruments.teledyne.TeledyneOscilloscope)

Provides the LeCroy T3DSO1204 Oscilloscope interface used to communicate with the instrument.

Use the LeCroy T3DSO1204 Oscilloscope Programmer’s Guide when you need more detail on the lower-level methods that talk directly to the scope.

This implementation derives from the shared `TeledyneOscilloscope` base class.

Attributes:
WRITE_INTERVAL_S: lower bound on the gap between consecutive commands. When a command arrives before WRITE_INTERVAL_S has elapsed since the prior command, execution waits until WRITE_INTERVAL_S seconds have passed. Some oscilloscope operations are slow enough that callers may still need to tune the sleep interval between commands. The default WRITE_INTERVAL_S is 10ms, but the best setting depends on both the command mix and connection type, so there is no single value that works everywhere. In practice, 10ms to 500ms has worked well, with the choice driven by commands and connection latency.

```python
from pymeasure.instruments.lecroy.lecroyT3DSO1204 import LeCroyT3DSO1204

scope = LeCroyT3DSO1204(resource)
scope.autoscale()
ch1_data_array, ch1_preamble = scope.download_waveform(source="C1", points=2000)
# ...
scope.shutdown()

```
