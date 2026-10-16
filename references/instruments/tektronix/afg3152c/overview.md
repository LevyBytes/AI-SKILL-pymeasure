# pymeasure.instruments.tektronix.AFG3152C

*class *pymeasure.instruments.tektronix.AFG3152C(*adapter*, *name='Tektronix AFG3152C arbitrary function generator'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the Tektronix AFG 3000 series arbitrary function generator, with one or two channels, and exposes a high-level interface for operating the instrument.

```python
from pymeasure.instruments.tektronix.afg3152c import AFG3152C

afg=AFG3152C("GPIB::1")        # AFG on GPIB 1
afg.reset()                    # Reset to default
afg.ch1.shape='sinusoidal'     # Sinusoidal shape
afg.ch1.unit='VPP'             # Sets CH1 unit to VPP
afg.ch1.amp_vpp=1              # Sets the CH1 level to 1 VPP
afg.ch1.frequency=1e3          # Sets the CH1 frequency to 1KHz
afg.ch1.enable()               # Enables the output from CH1

```
