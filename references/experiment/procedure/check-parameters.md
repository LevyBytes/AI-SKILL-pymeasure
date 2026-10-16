# pymeasure.experiment.procedure.Procedure.check_parameters

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_parameters()

Before the associated function runs, raises an exception if any parameter is missing. It verifies each value can be set and got, causing the value to be cast to the right format. Used as a @check_parameters decorator on startup.
