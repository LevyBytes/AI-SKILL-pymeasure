# pymeasure.instruments.teledyne.TeledyneT3AFG

*class *pymeasure.instruments.teledyne.TeledyneT3AFG(*adapter*, *name='Teledyne T3AFG'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Provides the Teledyne T3AFG series arbitrary waveform generator interface used to communicate with the instrument.

The initial target is T3AFG80. Lower end models may lack some features, and higher end model features are not covered here yet.

Future improvements (help welcomed):

- Add more OUTPut controls, such as Load and Polarity.

- Add more Basic Waveform controls, such as Period.

- Add frequency ranges per model

- Add channel coupling control
