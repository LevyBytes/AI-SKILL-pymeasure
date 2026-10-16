# pymeasure.instruments.agilent.agilentB1500.AgilentB1500.sweep_auto_abort

[Owning PyMeasure class, adapter and connection contract](overview.md)

sweep_auto_abort(*abort*, *post='START'*)

Turn the automatic abort function on or off. (`WM`)

The post measurement condition is configured as well.

Parameters:

- **abort** (*bool*) – Enable/Disable automatic abort

- **post** (*StaircaseSweepPostOutput*) – Post-measurement output, defaults to ‘Start’
