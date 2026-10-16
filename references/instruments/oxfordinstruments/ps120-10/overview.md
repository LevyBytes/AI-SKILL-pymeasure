# pymeasure.instruments.oxfordinstruments.PS120_10

*class *pymeasure.instruments.oxfordinstruments.PS120_10(*adapter*, *name='Oxford PS'*, ***kwargs*)

Bases: [`IPS120_10`](https://pymeasure.readthedocs.io/en/latest/api/instruments/oxfordinstruments/IPS120_10.html#pymeasure.instruments.oxfordinstruments.IPS120_10)

Models the Oxford Superconducting Magnet Power Supply PS 120-10.

```python
from pymeasure.instruments.oxfordinstruments.ps120_10 import PS120_10

ps = PS120_10("GPIB::25")   # Default channel for the IPS

ps.enable_control()         # Enables the power supply and remote control

ps.train_magnet([           # Train the magnet after it has been cooled-down
    (11.8, 1.0),
    (13.9, 0.4),
    (14.9, 0.2),
    (16.0, 0.1),
])

ps.set_field(12)            # Bring the magnet to 12 T. The switch heater will
                            # be turned off when the field is reached and the
                            # current is ramped back to 0 (i.e. persistent mode).

print(self.field)           # Print the current field (whether in persistent or
                            # non-persistent mode)

ps.set_field(0)             # Bring the magnet to 0 T. The persistent mode will be
                            # turned off first (i.e. current back to set-point and
                            # switch-heater on); afterwards the switch-heater will
                            # again be turned off.

ps.disable_control()        # Disables the control of the supply, turns off the
                            # switch-heater and clamps the output.

```

Parameters:

- **clear_buffer** - Boolean property controlling whether the instrument buffer is cleared during initialisation.

- **switch_heater_heating_delay** - Time in seconds (default is 20s) to wait after switch-heater turn-on before expecting the heater to be heated.

- **switch_heater_cooling_delay** - Time in seconds (default is 20s) to wait after switch-heater turn-off before expecting the heater to be cooled down.

- **field_range** - Numeric value or two-value tuple indicating the lowest and highest permitted magnetic fields. If a numeric value is supplied, the expected range is `-field_range` to `+field_range`.
