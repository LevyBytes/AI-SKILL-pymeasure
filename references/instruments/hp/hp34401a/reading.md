# pymeasure.instruments.hp.HP34401A.reading

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *reading*: Any*

Performs a measurement using the selected function.

Reading this property behaves like calling init_trigger(), waiting for completion, then fetching the reading(s).
