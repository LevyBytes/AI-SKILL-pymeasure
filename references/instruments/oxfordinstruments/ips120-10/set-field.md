# pymeasure.instruments.oxfordinstruments.IPS120_10.set_field

[Owning PyMeasure class, adapter and connection contract](overview.md)

set_field(*field*, *sweep_rate=None*, *persistent_mode_control=True*)

Sweeps the applied magnetic field to a requested magnitude. When `persistent_mode_control` permits it, persistent mode is disabled as necessary before the sweep and re-enabled once the target field is reached. For a new field set-point of 0, the instrument set-point is left unchanged and the IPS to zero function is used instead. In that 0T case, persistent mode is not re-enabled after the target is reached.

Parameters:

- **field** - New magnetic field set-point, in Tesla.

- **sweep_rate** - Numeric control for how quickly the magnetic field changes, in Tesla/minute. (default: `None`)

- **persistent_mode_control** - Boolean permission for switching persistent mode off before sweeping when needed and back on after the field is reached; if this is `False` while the system is already in persistent mode, `MagnetError` is raised and the magnetic field remains unchanged. (default: `True`)
