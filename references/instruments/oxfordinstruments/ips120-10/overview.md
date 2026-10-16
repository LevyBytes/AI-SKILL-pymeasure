# pymeasure.instruments.oxfordinstruments.IPS120_10

*class *pymeasure.instruments.oxfordinstruments.IPS120_10(*adapter*, *name='Oxford IPS'*, *clear_buffer=True*, *switch_heater_heating_delay=None*, *switch_heater_cooling_delay=None*, *field_range=None*, ***kwargs*)

Bases: [`OxfordInstrumentsBase`](https://pymeasure.readthedocs.io/en/latest/api/instruments/oxfordinstruments/base.html#pymeasure.instruments.oxfordinstruments.base.OxfordInstrumentsBase)

Models the Oxford Superconducting Magnet Power Supply IPS 120-10.

```python
from pymeasure.instruments.oxfordinstruments.ips120_10 import IPS120_10

ips = IPS120_10("GPIB::25")  # Default channel for the IPS

ips.enable_control()         # Enables the power supply and remote control

ips.train_magnet([           # Train the magnet after it has been cooled-down
    (11.8, 1.0),
    (13.9, 0.4),
    (14.9, 0.2),
    (16.0, 0.1),
])

ips.set_field(12)           # Bring the magnet to 12 T. The switch heater will
                            # be turned off when the field is reached and the
                            # current is ramped back to 0 (i.e. persistent mode).

print(self.field)           # Print the current field (whether in persistent or
                            # non-persistent mode)

ips.set_field(0)            # Bring the magnet to 0 T. The persistent mode will be
                            # turned off first (i.e. current back to set-point and
                            # switch-heater on); afterwards the switch-heater will
                            # again be turned off.

ips.disable_control()       # Disables the control of the supply, turns off the
                            # switch-heater and clamps the output.

```

Parameters:

- **clear_buffer** - Boolean setting for whether the instrument buffer gets cleared during initialisation. (default: `True`)

- **switch_heater_heating_delay** - Seconds to wait after enabling the switch-heater before considering the heater heated; the usual value is 20s. (default: `None`)

- **switch_heater_cooling_delay** - Seconds to wait after disabling the switch-heater before treating the heater as cooled down; the usual value is 20s. (default: `None`)

- **field_range** - Numeric limit or two-value tuple giving the minimum and maximum allowed magnetic fields. With one numeric value, the valid span is `-field_range` through `+field_range`. The default range is -7 to +7 Tesla. (default: `None`)
