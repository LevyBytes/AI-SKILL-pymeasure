# pymeasure.instruments.agilent.agilentB1500.AgilentB1500.sampling_auto_abort

[Owning PyMeasure class, adapter and connection contract](overview.md)

sampling_auto_abort(*abort*, *post='Bias'*)

Turn the automatic abort function on or off. (`MSC`)

The post measurement condition is configured as well.

Parameters:

- **abort** (*bool*) – Enable/Disable automatic abort

- **post** (*SamplingPostOutput*) – Post-measurement output, defaults to ‘Bias’
