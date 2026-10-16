# pymeasure.instruments.oxfordinstruments.ITC503.sweep_table

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *sweep_table*: Any*

Property for working with entries in the sweep table. `ITC503.x_pointer` and `ITC503.y_pointer` (or `ITC503.pointer`) select the table location to read or set.

The x-pointer chooses the sweep step (1 to 16), and the y-pointer chooses the parameter:

| y-pointer | parameter |
| --- | --- |
| 1 | set-point temperature |
| 2 | sweep-time to set-point |
| 3 | hold-time at set-point |
