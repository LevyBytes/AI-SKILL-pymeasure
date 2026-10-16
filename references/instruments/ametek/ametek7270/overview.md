# pymeasure.instruments.ametek.Ametek7270

*class *pymeasure.instruments.ametek.Ametek7270(*adapter*, *name='Ametek DSP 7270'*, *read_termination='\x00'*, *write_termination='\x00'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Class representing the Ametek DSP 7270 lockin amplifier.

For this instrument, certain measurements are available only in particular Reference modes; see `set_reference_mode()`. Calling them in the wrong mode raises errors.
