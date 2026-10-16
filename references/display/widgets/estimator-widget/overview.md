# pymeasure.display.widgets.estimator_widget.EstimatorWidget

*class *pymeasure.display.widgets.estimator_widget.EstimatorWidget(*parent=None*)

Bases: `QWidget`

Widget for presenting preliminary estimates for a measurement procedure.

This widget uses the get_estimates method supplied by the [`Procedure`](https://pymeasure.readthedocs.io/en/latest/api/experiment/procedure.html#pymeasure.experiment.procedure.Procedure) class. get_estimates should produce a list of tuples, with each tuple holding two strings: one label and one estimate.

When `SequencerWidget` is present as well, the get_estimates Implementation can request two keyword arguments: sequence for the active sequencer and sequence_length for its length.
