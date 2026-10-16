# pymeasure.instruments.hp.HP8753E

*class *pymeasure.instruments.hp.HP8753E(*adapter=None*, *name=None*, *min_frequency=30000.0*, *max_frequency=6000000000.0*, *min_power=-70*, *max_power=10*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the HP8753E Vector Network Analyzer and exposes a high-level interface for sweeps over scattering or measurement parameters.

Parameters:

- **name** - Optionally set the instrument name (str). (default: `None`)

- **min_frequency** - Optional minimum validator applied during initialization for HP8753E.start_frequency, HP8753E.stop_frequency, HP8753E.span_frequency, HP8753E.center_frequency (float in Hz). (default: `30000.0`)

- **max_frequency** - Optional maximum validator applied during initialization for HP8753E.start_frequency, HP8753E.stop_frequency, HP8753E.span_frequency, HP8753E.center_frequency (float in Hz). (default: `6000000000.0`)

- **min_power** - Optional minimum validator applied to HP8753E.power during initialization (float in dBm). (default: `-70`)

- **max_power** - Optional maximum validator applied to HP8753E.power during initialization (float in dBm). (default: `10`)
