# pymeasure.experiment.listeners.Recorder.stop

[Owning PyMeasure class, adapter and connection contract](overview.md)

stop()

Stop the listener.

Requests thread termination, then waits for the thread to finish. If this is not called before the application exits, records may remain on the queue and therefore may not be processed.
