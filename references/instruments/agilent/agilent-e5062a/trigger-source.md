# pymeasure.instruments.agilent.AgilentE5062A.trigger_source

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *trigger_source*: Any*

Set or read trigger source (str). Documentation-defined values are:

- INT: Selects internal triggering, which automatically produces continuous triggers (default).

- EXT: Creates a trigger from an external trigger signal received through the Ext Trig connector or handler interface.

- MAN: Creates a trigger when the front-panel [Trigger] - Trigger key operation is run.

- BUS: Creates a trigger when `*TRG` is executed.
