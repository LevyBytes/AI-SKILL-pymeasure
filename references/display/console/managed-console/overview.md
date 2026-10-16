# pymeasure.display.console.ManagedConsole

*class *pymeasure.display.console.ManagedConsole(*procedure_class*, *log_channel=''*, *log_level=20*, ***kwargs*)

Bases: `QCoreApplication`

Console-oriented foundation for managing experiments.

Parameters for `__init__` constructor.

Parameters:

- **procedure_class** – class for the procedure that defines the experiment; see [`Procedure`](https://pymeasure.readthedocs.io/en/latest/api/experiment/procedure.html#pymeasure.experiment.procedure.Procedure).

- **log_channel** – `logging.Logger` object used for emitted log output (default: `''`).

- **log_level** – logging level (default: `20`)

- **kwargs** – extra keyword arguments forwarded into the `ConsoleArgumentParser` constructor.
