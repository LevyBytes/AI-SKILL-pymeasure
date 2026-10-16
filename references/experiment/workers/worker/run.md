# pymeasure.experiment.workers.Worker.run

[Owning PyMeasure class, adapter and connection contract](overview.md)

run()

Method that represents the thread's activity.

You may override it in a subclass. In the standard run() method, if a target argument supplied a callable object to the object's constructor, that callable is invoked with sequential and keyword arguments from args and kwargs, respectively.
