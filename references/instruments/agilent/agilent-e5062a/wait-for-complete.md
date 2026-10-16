# pymeasure.instruments.agilent.AgilentE5062A.wait_for_complete

[Owning PyMeasure class, adapter and connection contract](overview.md)

wait_for_complete(*attempt=1*, *max_attempts=20*)

Wait, potentially for a long interval, for the synchronization bit. Use with agilentE5062A.trigger_single() when a single sweep must finish before continuing.
