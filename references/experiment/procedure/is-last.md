# pymeasure.experiment.procedure.Procedure.is_last

[Owning PyMeasure class, adapter and connection contract](overview.md)

is_last()

Checks whether this procedure is last in the queue.

A worker must monkey patch this method to supply functionality.

Return type:

`bool`

Returns:

bool: True when the procedure is last in the queue, otherwise False.
