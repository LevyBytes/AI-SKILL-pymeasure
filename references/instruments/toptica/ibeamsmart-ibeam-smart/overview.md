# pymeasure.instruments.toptica.ibeamsmart.IBeamSmart

*class *pymeasure.instruments.toptica.ibeamsmart.IBeamSmart(*adapter*, *name='Toptica IBeam Smart laser diode'*, *baud_rate=115200*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

IBeam Smart laser diode

Consult the manual for how the diode driver channels are used.

```python
from pymeasure.instruments.toptica.ibeamsmart import IBeamSmart

laser = IBeamSmart("SomeResourceString")
laser.emission = True
laser.ch_2.power = 1000  # µW
laser.ch_2.enabled = True
laser.shutdown()

```

Parameters:

- **adapter** – pyvisa resource name, or an adapter instance.

- **baud_rate** – Baud rate configured in the instrument. (default: `115200`)

- ****kwargs** – Any key-word argument accepted by VISAAdapter.
