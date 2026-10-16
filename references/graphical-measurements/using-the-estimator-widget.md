# Using the estimator widget

An [`EstimatorWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.estimator_widget.EstimatorWidget) is available for defining and calculating measurement estimates. The widget turns on automatically after `get_estimates` is added to the `Procedure`.

The smallest useful `get_estimates` implementation simply returns the estimated measurement duration in seconds, as an `int` or a `float`. In the example from the Using the ManagedWindow section, update the `Procedure` to:

```python
from pymeasure.experiment.procedure import Procedure

class RandomProcedure(Procedure):

    # ...

    def get_estimates(self, sequence_length=None, sequence=None):

        return self.iterations * self.delay

```

That change places the estimator widget in the left dock. In this configuration, duration and finishing-time for one measurement are always visible. If SequencerWidget is active as well, the full sequence length, duration, and finishing-time are shown too.

For broader estimate displays, `get_estimates` may instead return a list of tuples, for example duration, filesize, finishing-time, and other values. Each tuple contains two strings: first the estimate name (label), then the estimate value.

The example from the Using the ManagedWindow section can be adapted by changing the `Procedure` to:

```python
from pymeasure.experiment.procedure import Procedure

class RandomProcedure(Procedure):

    # ...

    def get_estimates(self, sequence_length=None, sequence=None):

        duration = self.iterations * self.delay

        estimates = [
            ("Duration", "%d s" % int(duration)),
            ("Number of lines", "%d" % int(self.iterations)),
            ("Sequence length", str(sequence_length)),
            ('Measurement finished at', str(datetime.now() + timedelta(seconds=duration))),
        ]

        return estimates

```

That version also places the estimator widget in the dock on the left.

 (Figure: Estimator widget example)

After the widget is initialized, both the estimate label and the estimate value can still be changed; however, the number of estimates is fixed.

The function implementation does not have to declare keyword arguments; they are supplied only when the signature requests them, so `def get_estimates(self)` is valid. The accepted names are `sequence`, containing the complete sequencer sequence when one exists, and `sequence_length`, an integer length for that sequence when available. Without a sequencer, or when parsing the sequence fails, both `sequence` and `sequence_length` are set to `None`.

The estimates refresh automatically every 2 seconds. The “Update continuously”-checkbox controls that interval and has three states: off (no refresh), auto-update every 2 seconds (default), and auto-update every 100 milliseconds. When continuous updating is disabled, use the “update”-button to refresh manually.
