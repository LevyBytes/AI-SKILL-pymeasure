# pymeasure.display.windows.managed_window.ManagedWindowBase.queue

[Owning PyMeasure class, adapter and connection contract](constructor-widgets.md)

queue(*procedure=None*)

Queues a measurement using the parameters currently in the input-widget.

Semi-abstract method. Child classes must override it when filename- and directory-inputs are disabled. If those inputs remain enabled, overriding is optional and may support custom naming, input processing, or other features.

Implementations must pass an `experiment` ([`Experiment`](https://pymeasure.readthedocs.io/en/latest/api/experiment/experiment.html#pymeasure.experiment.experiment.Experiment)) object to `self.manager.queue(experiment)`; that object contains the [`Results`](https://pymeasure.readthedocs.io/en/latest/api/experiment/results.html#pymeasure.experiment.results.Results) and [`Procedure`](https://pymeasure.readthedocs.io/en/latest/api/experiment/procedure.html#pymeasure.experiment.procedure.Procedure) that will run.

A basic implementation does not need the optional procedure argument; it is required when using [`SequencerWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.sequencer_widget.SequencerWidget).

For example:

```python
from pymeasure.experiment.results import Results

def queue(self):
    filename = unique_filename('results', prefix="data") # from pymeasure.experiment

    procedure = self.make_procedure() # Procedure class was passed at construction
    results = Results(procedure, filename)
    experiment = self.new_experiment(results)

    self.manager.queue(experiment)

```
