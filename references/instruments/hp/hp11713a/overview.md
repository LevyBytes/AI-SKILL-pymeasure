# pymeasure.instruments.hp.HP11713A

## HP 11713A Attenuator/Switch Driver

### HP 11713A Attenuator/Switch Driver

 *class *pymeasure.instruments.hp.HP11713A(*adapter*, *name='Hewlett-Packard HP11713A'*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the HP 11713A Switch and Attenuator Driver and exposes a high-level interface for instrument control.

An attenuator is typically connected to X, Y, or both X and Y. For simpler attenuator-driver control, choose an attenuator type with the `ATTENUATOR_X` or `ATTENUATOR_Y` attribute. hp11713a includes separate default attenuator mappings. Once the attenuator type is selected, the `attenuation_x` and/or `attenuation_y` methods can set the switch driver to the value matching the requested attenuation. Attenuation inputs are rounded.

```python
from pymeasure.instruments.hp import HP11713A
from pymeasure.instruments.hp.hp11713a import Attenuator_110dB

sd = HP11713A("GPIB::1")

sd.ATTENUATOR_Y = Attenuator_110dB
sd.attenuation_y(10)
sd.ch_0.enabled = True

```
