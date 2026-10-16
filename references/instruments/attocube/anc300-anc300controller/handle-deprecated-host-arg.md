# pymeasure.instruments.attocube.anc300.ANC300Controller.handle_deprecated_host_arg

This contract is documented in [PyMeasure v0.16.0](https://github.com/pymeasure/pymeasure/blob/v0.16.0/pymeasure/instruments/attocube/anc300.py). It is absent from the current development source; check the installed release before using it.

[Owning PyMeasure class, adapter and connection contract](overview.md)

handle_deprecated_host_arg(*adapter*, *kwargs*)

Normalizes user input for __init__ so it matches the current __init__ signature. It exists to keep outdated (deprecated) code working and is isolated so future removal is simpler. Removal note: delete this function and make the adapter argument in __init__ non-optional.

Parameters:

**kwargs** (*dict*) - keyword arguments passed into __init__, including the deprecated host argument.

Return str:

resource string for the VISAAdapter
