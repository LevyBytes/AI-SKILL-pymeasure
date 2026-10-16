# pymeasure.instruments.heidenhain.ND287.position

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *position*: Any*

Measure the encoder current position (float). The get_process maps the returned value to a float in the units specified by `ND287.units`. Because the mapping varies slightly by unit, get_process is adjusted dynamically.(dynamic)
