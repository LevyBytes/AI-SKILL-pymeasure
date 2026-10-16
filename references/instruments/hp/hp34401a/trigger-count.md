# pymeasure.instruments.hp.HP34401A.trigger_count

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *trigger_count*: Any*

Sets how many triggers are accepted before the instrument returns to the ?idle? state.

Valid values: 1 to 50000, ?MIN?, ?MAX?, ?INF?. The INFinite parameter makes the multimeter keep accepting triggers continuously; send a device clear to return to the ?idle? state.
