# pymeasure.instruments.keysight.KeysightN7776C

*class *pymeasure.instruments.keysight.KeysightN7776C(*adapter*, *name='N7776C Tunable Laser Source'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Describes the Keysight N7776C Tunable Laser Source interface.

```python
laser = N7776C(address)
laser.sweep_wl_start = 1550
laser.sweep_wl_stop = 1560
laser.sweep_speed = 1
laser.sweep_mode = 'CONT'
laser.output_enabled = 1
while laser.sweep_state == 1:
    log.info('Sweep in progress.')
laser.output_enabled = 0

```
