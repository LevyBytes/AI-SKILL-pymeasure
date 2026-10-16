# pymeasure.instruments.oxfordinstruments.base.OxfordInstrumentsBase

*class *pymeasure.instruments.oxfordinstruments.base.OxfordInstrumentsBase(*adapter*, *name='OxfordInstruments Base'*, *max_attempts=5*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Base instrument class for Oxford Instruments devices.

Validates replies received from instruments.

Parameters:

- **adapter** - A string, integer, or [`Adapter`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.Adapter) subclass object

- **name** (*string*) - Instrument name, often defaulting to the model designation.

- **max_attempts** - Integer specifying how many tries may be made to obtain a valid query response (default: `5`)

- ****kwargs** - When `adapter` is a string or integer, additional arguments are passed to [`VISAAdapter`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.VISAAdapter) (see that documentation for details). Otherwise, they are discarded.
