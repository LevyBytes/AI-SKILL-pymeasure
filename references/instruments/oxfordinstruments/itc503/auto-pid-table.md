# pymeasure.instruments.oxfordinstruments.ITC503.auto_pid_table

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *auto_pid_table*: Any*

Property for manipulating entries in the auto-pid table. `ITC503.x_pointer` and `ITC503.y_pointer` (or `ITC503.pointer`) choose the table location to write or read.

The x-pointer identifies the table entry (1 to 16), while the y-pointer chooses the parameter:

| y-pointer | parameter |
| --- | --- |
| 1 | upper temperature limit |
| 2 | proportional band |
| 3 | integral action time |
| 4 | derivative action time |
