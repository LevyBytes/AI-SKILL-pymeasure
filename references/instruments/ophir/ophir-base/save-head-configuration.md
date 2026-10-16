# pymeasure.instruments.ophir.ophir_base.OphirBase.save_head_configuration

[Owning PyMeasure class, adapter and connection contract](overview.md)

save_head_configuration(*config*)

Save selected sensor configuration. :rtype: `None`

- ‘S’ for startup

- ‘C’ for calibration

- 'R' means Responsive for thermopile sensors.

The response is "*SAVED", "*UNCHANGED", or "?FAILED".
