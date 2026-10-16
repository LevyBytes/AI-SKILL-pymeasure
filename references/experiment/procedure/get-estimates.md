# pymeasure.experiment.procedure.Procedure.get_estimates

[Owning PyMeasure class, adapter and connection contract](overview.md)

get_estimates()

Returns estimates for display in the EstimatorWidget. Subclasses must reimplement it. The return value should be an int or float duration in seconds, or a list containing one tuple per estimate. Each tuple should contain two strings: first the estimate label, then the estimate text to display.
