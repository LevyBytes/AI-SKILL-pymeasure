# Results, Procedure, Experiment, Workers ...

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: pymeasure.experiment; Results class; Procedure class; Experiment class; Worker class; Listener class.

## pymeasure.experiment

### pymeasure.experiment

This section gives package-specific reference material for its classes and methods.

- [Experiment class](https://pymeasure.readthedocs.io/en/latest/api/experiment/experiment.html)
  - [`Experiment`](https://pymeasure.readthedocs.io/en/latest/api/experiment/experiment.html#pymeasure.experiment.experiment.Experiment)
  - [`create_filename()`](https://pymeasure.readthedocs.io/en/latest/api/experiment/experiment.html#pymeasure.experiment.experiment.create_filename)
  - [`get_array()`](https://pymeasure.readthedocs.io/en/latest/api/experiment/experiment.html#pymeasure.experiment.experiment.get_array)
  - [`get_array_steps()`](https://pymeasure.readthedocs.io/en/latest/api/experiment/experiment.html#pymeasure.experiment.experiment.get_array_steps)
  - [`get_array_zero()`](https://pymeasure.readthedocs.io/en/latest/api/experiment/experiment.html#pymeasure.experiment.experiment.get_array_zero)

- [Listener class](https://pymeasure.readthedocs.io/en/latest/api/experiment/listeners.html)
  - [`Listener`](https://pymeasure.readthedocs.io/en/latest/api/experiment/listeners.html#pymeasure.experiment.listeners.Listener)
  - [`Monitor`](https://pymeasure.readthedocs.io/en/latest/api/experiment/listeners.html#pymeasure.experiment.listeners.Monitor)
  - [`Recorder`](https://pymeasure.readthedocs.io/en/latest/api/experiment/listeners.html#pymeasure.experiment.listeners.Recorder)

- [Procedure class](https://pymeasure.readthedocs.io/en/latest/api/experiment/procedure.html)
  - [`Procedure`](https://pymeasure.readthedocs.io/en/latest/api/experiment/procedure.html#pymeasure.experiment.procedure.Procedure)
  - [`UnknownProcedure`](https://pymeasure.readthedocs.io/en/latest/api/experiment/procedure.html#pymeasure.experiment.procedure.UnknownProcedure)

- [Parameter classes](https://pymeasure.readthedocs.io/en/latest/api/experiment/parameters.html)
  - [`BooleanParameter`](https://pymeasure.readthedocs.io/en/latest/api/experiment/parameters.html#pymeasure.experiment.parameters.BooleanParameter)
  - [`FloatParameter`](https://pymeasure.readthedocs.io/en/latest/api/experiment/parameters.html#pymeasure.experiment.parameters.FloatParameter)
  - [`IntegerParameter`](https://pymeasure.readthedocs.io/en/latest/api/experiment/parameters.html#pymeasure.experiment.parameters.IntegerParameter)
  - [`ListParameter`](https://pymeasure.readthedocs.io/en/latest/api/experiment/parameters.html#pymeasure.experiment.parameters.ListParameter)
  - [`Measurable`](https://pymeasure.readthedocs.io/en/latest/api/experiment/parameters.html#pymeasure.experiment.parameters.Measurable)
  - [`Metadata`](https://pymeasure.readthedocs.io/en/latest/api/experiment/parameters.html#pymeasure.experiment.parameters.Metadata)
  - [`Parameter`](https://pymeasure.readthedocs.io/en/latest/api/experiment/parameters.html#pymeasure.experiment.parameters.Parameter)
  - [`PhysicalParameter`](https://pymeasure.readthedocs.io/en/latest/api/experiment/parameters.html#pymeasure.experiment.parameters.PhysicalParameter)
  - [`VectorParameter`](https://pymeasure.readthedocs.io/en/latest/api/experiment/parameters.html#pymeasure.experiment.parameters.VectorParameter)

- [Worker class](https://pymeasure.readthedocs.io/en/latest/api/experiment/workers.html)
  - [`Worker`](https://pymeasure.readthedocs.io/en/latest/api/experiment/workers.html#pymeasure.experiment.workers.Worker)

- [Results class](https://pymeasure.readthedocs.io/en/latest/api/experiment/results.html)
  - [`CSVFormatter`](https://pymeasure.readthedocs.io/en/latest/api/experiment/results.html#pymeasure.experiment.results.CSVFormatter)
  - [`Results`](https://pymeasure.readthedocs.io/en/latest/api/experiment/results.html#pymeasure.experiment.results.Results)
  - [`replace_placeholders()`](https://pymeasure.readthedocs.io/en/latest/api/experiment/results.html#pymeasure.experiment.results.replace_placeholders)
  - [`unique_filename()`](https://pymeasure.readthedocs.io/en/latest/api/experiment/results.html#pymeasure.experiment.results.unique_filename)

## Results class

### Results class

 *class *pymeasure.experiment.results.CSVFormatter(*columns*, *delimiter=','*)

Formatter of data results

 format(*record*)

Formats a record as csv.

Parameters:

**record** (*dict*) – record to format.

Returns:

a string

 *class *pymeasure.experiment.results.Results(*procedure*, *data_filename*)

The Results class offers an interface for data reads and writes tied to a [`Procedure`](https://pymeasure.readthedocs.io/en/latest/api/experiment/procedure.html#pymeasure.experiment.procedure.Procedure) object.

Variables:

-

**COMMENT** - Character that marks a comment (default: #)

-

**DELIMITER** - Character separating data fields (default: ,)

-

**LINE_BREAK** - Character inserted for line breaks (default n)

-

**CHUNK_SIZE** - Length of the data chunk to read

Parameters:

-

**procedure** – Procedure object

-

**data_filename** - Data filename where data is already stored or should be stored

 format(*data*)

Produces the formatted data string that will be written to a file.

 header()

Produces the datafile header text needed to reconstruct the procedure.

 labels()

Produces the column labels as text for writing to the file.

 *static *load(*data_filename*, *procedure_class=None*)

Creates a Results object linked to its Procedure object and data.

 metadata()

Builds the metadata header text to write into the datafile.

 parse(*line*)

Parses the line into a dictionary of data values.

 *static *parse_header(*header*, *procedure_class=None*)

Builds a Procedure object using the parameters defined in the header text.

 reload()

Fully reloads the file data and ignores any comment changes.

 store_metadata()

Adds the metadata header, when present, into the datafile.

 pymeasure.experiment.results.replace_placeholders(*string*, *procedure*, *date_format='%Y_%m_%d'*, *time_format='%H_%M_%S'*)

Substitutes values from procedure parameters into placeholders in a string.

Replaces placeholders in the supplied string with values from the associated parameters, taken from the procedure. The standard python string.format syntax is used. Besides procedure parameters, referenced by their full names, the optional placeholders "date" and "time" are also available.

Parameters:

-

**string** - String whose placeholders should be substituted. Python string.format syntax applies; for example, "{Parameter Name}" inserts a FloatParameter named "Parameter Name", and "{Parameter Name:.2f}" also applies explicit formatting to the parameter.

-

**procedure** - Procedure used as the source of parameter values.

-

**date_format** - String describing the format for the extra placeholder "date". (default: `'%Y_%m_%d'`)

-

**time_format** - String describing the format for the extra placeholder "time". (default: `'%H_%M_%S'`)

 pymeasure.experiment.results.unique_filename(*directory*, *prefix='DATA'*, *suffix=''*, *ext='csv'*, *dated_folder=False*, *index=True*, *datetimeformat='%Y-%m-%d'*, *procedure=None*)

Creates a unique filename from the directory and prefix.

## Procedure class

### Procedure class

 *class *pymeasure.experiment.procedure.Procedure(***kwargs*)

Provides the base Procedure class used to organize experiment execution. Run procedures through Workers so asynchronous execution is managed correctly.

```python
procedure = Procedure()
results = Results(procedure, data_filename)
worker = Worker(results, port)
worker.start()

```

Subclasses should implement startup, execute, and shutdown as required. shutdown is still called when execute hits a software exception or an abort event.

When keyword arguments are supplied, the object receives them as attributes.

 check_parameters()

Before the associated function runs, raises an exception if any parameter is missing. It verifies each value can be set and got, causing the value to be cast to the right format. Used as a @check_parameters decorator on startup.

 evaluate_metadata()

Evaluates every Metadata object and fixes each one to its current value.

 execute()

Performs the measurement commands. After this method, shutdown always runs, including when Exceptions are raised.

 gen_measurement()

Creates the MEASURE and DATA_COLUMNS variables used by get_datapoint.

 get_estimates()

Returns estimates for display in the EstimatorWidget. Subclasses must reimplement it. The return value should be an int or float duration in seconds, or a list containing one tuple per estimate. Each tuple should contain two strings: first the estimate label, then the estimate text to display.

 is_last()

Checks whether this procedure is last in the queue.

A worker must monkey patch this method to supply functionality.

Return type:

`bool`

Returns:

bool: True when the procedure is last in the queue, otherwise False.

 metadata_objects()

Returns a dictionary containing every Metadata object.

 parameter_objects()

Returns a dictionary containing every Parameter object, collecting current values that are absent from the default definitions.

 parameter_values()

Returns a dictionary containing every Parameter value, collecting current values that are absent from the default definitions.

 parameters_are_set()

Returns True when every parameter is set.

 *static *parse_columns(*columns*)

Parses columns that include units in parentheses. For each column, when matching parentheses hold text with no spaces, the enclosed value is treated as a Pint unit. Example: "Source Voltage (V)" is parsed and matched to `Unit('volt')`. Raises an error if the parsed value is not defined in the Pint unit registry. Returns a dictionary mapping matched columns to their units.

Parameters:

**columns** - List of columns to parse.

Returns:

Dictionary of columns with Pint units.

 *classmethod *placeholder_names()

Collects all eligible placeholder names (parameters & metadata).

 placeholder_objects()

Collects every eligible placeholder (parameters & metadata) and its value into a dict.

 refresh_parameters()

Forces all parameters to be re-cast and updated in the meta dictionary.

 set_parameters(*parameters*, *except_missing=True*)

Sets parameters from a dictionary and, if except_missing is True, raises an exception when extra parameters are included.

 shutdown()

Runs the shutdown commands needed to put instruments into a safe state. This method always runs at the end.

 startup()

Runs commands required at measurement start-up.

 *class *pymeasure.experiment.procedure.UnknownProcedure(*parameters*)

Covers the case where a `Procedure` object cannot be imported while the [`Results`](https://pymeasure.readthedocs.io/en/latest/api/experiment/results.html#pymeasure.experiment.results.Results) class is loading.

 startup()

Runs commands required at measurement start-up.

## Experiment class

### Experiment class

Experiment class is designed for Jupyter notebook use.

 *class *pymeasure.experiment.experiment.Experiment(*title*, *procedure*, *analyse=<function Experiment.<lambda>>*)

Bases: `object`

Class that starts logging and creates/runs the results and worker processes.

```python
procedure = Procedure()
experiment = Experiment(title, procedure)
experiment.start()
experiment.plot_live('x', 'y', style='.-')

for a multi-subplot graph:

import pylab as pl
ax1 = pl.subplot(121)
experiment.plot('x','y',ax=ax1)
ax2 = pl.subplot(122)
experiment.plot('x','z',ax=ax2)
experiment.plot_live()

```

Variables:

**value** - The parameter value

Parameters:

-

**title** – The experiment title

-

**procedure** – The procedure object

-

**analyse** - Post-analysis function that receives a pandas dataframe and returns it with added analysed columns. Analysed results are exposed through experiment.data; raw data remains available through experiment.results.data. (default: `<function Experiment.<lambda> at 0x7aa58c705bc0>`)

-

**_data_timeout** - Time limit controlling how long live plotting waits for datapoints.

 clear_plot()

Clears the figures and plot lists.

 *property *data

Data property returns analysed data when an analyse function is defined; otherwise it returns the raw data.

 plot(**args*, ***kwargs*)

Plots results from the experiment.data pandas dataframe and stores the plots in a plots list attribute.

 plot_live(**args*, ***kwargs*)

Live plotting loop for Jupyter notebook that automatically refreshes inline matplotlib graph(s). It either creates a new plot as requested by the input arguments or updates existing plot(s).

 start()

Start the worker

 update_line(*ax*, *hl*, *xname*, *yname*)

Updates a line in a matplotlib graph using new data.

 update_plot()

Refreshes the plots list with new data from the experiment.data pandas dataframe.

 wait_for_data()

Waits until the data attribute contains datapoints.

 pymeasure.experiment.experiment.create_filename(*title*)

Creates a new filename using the style from the config file. If no config is specified, it creates a temporary file.

 pymeasure.experiment.experiment.get_array(*start*, *stop*, *step*)

Returns a numpy array spanning start to stop.

 pymeasure.experiment.experiment.get_array_steps(*start*, *stop*, *numsteps*)

Returns a numpy array spanning start to stop in numsteps.

 pymeasure.experiment.experiment.get_array_zero(*maxval*, *step*)

Returns a numpy array moving from 0 to maxval to -maxval to 0.

## Worker class

### Worker class

 *class *pymeasure.experiment.workers.Worker(*results*, *log_queue=None*, *log_level=20*, *port=None*)

Bases: `StoppableThread`

Worker executes the procedure and publishes procedure/status details through a ZMQ TCP port. In a child thread, a Recorder runs to write the results to

 emit(*topic*, *record*)

Emits data for a given topic over TCP.

 handle_abort()

 handle_batch_record(*record*)

 handle_error()

 handle_record(*record*)

 is_last()

 join(*timeout=0*)

Joins the current thread and, after timeout if needed, forces it to stop.

Parameters:

**timeout** (`int`) - Timeout duration, in seconds (default: `0`)

 run()

Method that represents the thread's activity.

You may override it in a subclass. In the standard run() method, if a target argument supplied a callable object to the object's constructor, that callable is invoked with sequential and keyword arguments from args and kwargs, respectively.

 shutdown()

 update_status(*status*)

## Listener class

### Listener class

 *class *pymeasure.experiment.listeners.Listener(*port*, *topic=''*, *timeout=0.01*)

Bases: `StoppableThread`

Base class for Threads that listen on a ZMQ TCP port for incoming messages and support stopping through a thread-safe method call.

 message_waiting()

Checks for a message, waiting no longer than timeout.

 receive(*flags=0*)

 *class *pymeasure.experiment.listeners.Monitor(*results*, *queue*)

Bases: `QueueListener`

 *class *pymeasure.experiment.listeners.Recorder(*results*, *queue*, ***kwargs*)

Bases: `QueueListener`

Recorder reads the initial Results for a filepath and appends data received over a queue. The queue prevents data loss between the Recorder and Worker.

 stop()

Stop the listener.

Requests thread termination, then waits for the thread to finish. If this is not called before the application exits, records may remain on the queue and therefore may not be processed.
