# pymeasure.instruments.teledyne.TeledyneOscilloscope

*class *pymeasure.instruments.teledyne.TeledyneOscilloscope(*adapter*, *name='Teledyne Oscilloscope'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Abstract superclass for Teledyne Lecroy oscilloscope implementations.

Teledyne oscilloscope models expose broadly comparable controls, so shared behavior is collected in this base class. Individual instruments may still differ or expose conflicting interface details.

Attributes:

WRITE_INTERVAL_S: shortest allowed gap between successive commands. When a new command arrives sooner than WRITE_INTERVAL_S after the last one, execution waits until WRITE_INTERVAL_S seconds have elapsed. Since some oscilloscope operations take noticeable time, users may need to adjust the inter-command delay. The WRITE_INTERVAL_S default is 10ms, but the best value depends strongly on the command mix and transport. In practice, values from 10ms through 500ms second have worked, depending on connection latency and the operations being issued.
