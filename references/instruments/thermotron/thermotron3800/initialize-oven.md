# pymeasure.instruments.thermotron.Thermotron3800.initialize_oven

[Owning PyMeasure class, adapter and connection contract](overview.md)

initialize_oven(*wait=True*)

Initialize the oven, with an optional delay before continuing.

After oven initialization, the manufacturer advises waiting 3 seconds. Keep the optional `wait` variable true unless user code already provides that 3 second pause. Timing is divided as 1 second in the write function plus 2 seconds from this initialize_oven wait option.

Returns:

`None` – None
