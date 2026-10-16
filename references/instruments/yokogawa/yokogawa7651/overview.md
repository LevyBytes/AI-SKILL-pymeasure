# pymeasure.instruments.yokogawa.Yokogawa7651

*class *pymeasure.instruments.yokogawa.Yokogawa7651(*adapter*, *name='Yokogawa 7651 Programmable DC Source'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Instrument model for the Yokogawa 7651 Programmable DC Source, with a high-level interface for interacting with the instrument.

```python
from pymeasure.instruments.yokogawa.yokogawa7651 import Yokogawa7651

yoko = Yokogawa7651("GPIB::1")

yoko.apply_current()                # Sets up to source current
yoko.source_current_range = 10e-3   # Sets the current range to 10 mA
yoko.compliance_voltage = 10        # Sets the compliance voltage to 10 V
yoko.source_current = 0             # Sets the source current to 0 mA

yoko.enable_source()                # Enables the current output
yoko.ramp_to_current(5e-3)          # Ramps the current to 5 mA

yoko.shutdown()                     # Ramps the current to 0 mA and disables output

```
