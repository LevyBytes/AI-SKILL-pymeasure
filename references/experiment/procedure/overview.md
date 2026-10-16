# pymeasure.experiment.procedure.Procedure

*class *pymeasure.experiment.procedure.Procedure(***kwargs*)

Provides the base Procedure class used to organize experiment execution. Run procedures through Workers so asynchronous execution is managed correctly.

```python
from pymeasure.experiment.procedure import Procedure
from pymeasure.experiment.results import Results
from pymeasure.experiment.workers import Worker

procedure = Procedure()
results = Results(procedure, data_filename)
worker = Worker(results, port)
worker.start()

```

Subclasses should implement startup, execute, and shutdown as required. shutdown is still called when execute hits a software exception or an abort event.

When keyword arguments are supplied, the object receives them as attributes.
