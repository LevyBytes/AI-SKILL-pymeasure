# pymeasure.instruments.velleman.VellemanK8090

*class *pymeasure.instruments.velleman.VellemanK8090(*adapter*, *name='Velleman K8090'*, *timeout=100*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Use this for the Velleman K8090 relay board.

Consult the "K8090/VM8090 PROTOCOL MANUAL" for serial command details.

Communication uses serial USB, with fixed IO settings:

| Baud rate | 19200 |
| --- | --- |
| Data bits | 8 |
| Parity | None |
| Stop bits | 1 |
| Flow control | None |

Prefer a short timeout because the device does not reliably emit status messages, and serial timeouts can happen during normal use.

Use the class like:

```python
from pymeasure.instruments.velleman import VellemanK8090, VellemanK8090Switches as Switches

instrument = VellemanK8090("ASRL1::INSTR")

# Get status update from device
last_on, curr_on, time_on = instrument.status

# Toggle a selection of channels on
instrument.switch_on = Switches.CH3 | Switches.CH4 | Switches.CH5

```
