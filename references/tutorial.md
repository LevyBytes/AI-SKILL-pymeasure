# Procedure

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Making a measurement; Tutorials.

## Making a measurement

### Making a measurement

This section demonstrates how to use PyMeasure to collect a current-voltage (IV) characteristic with a Keithley 2400. The same pattern applies even without that hardware: begin with a plain script, then move the workflow into [`Procedure`](https://pymeasure.readthedocs.io/en/latest/api/experiment/procedure.html#module-pymeasure.experiment.procedure) objects, and finally run the measurement from a graphical interface.

### Using scripts

A script is the fastest starting point for a PyMeasure measurement. For the IV characteristic example, use this sequence:

1.

Import the necessary packages

2.

Choose the input parameters that define the measurement

3.

Configure source_current and measure_voltage parameters

4.

Connect to the Keithley 2400

5.

Configure the instrument for the IV characteristic

6.

Create arrays for storing measured results

7.

Iterate over current points, take the voltage reading, and record it

8.

Write the completed data set to a CSV file

9.

Shutdown the instrument

The same workflow appears in code below.

```python
# Import necessary packages
from pymeasure.instruments.keithley import Keithley2400
import numpy as np
import pandas as pd
from time import sleep

# Set the input parameters
data_points = 50
averages = 10
max_current = 0.001
min_current = -max_current

# Set source_current and measure_voltage parameters
current_range = 10e-3  # in Amps
compliance_voltage = 10  # in Volts
measure_nplc = 0.1  # Number of power line cycles
voltage_range = 1  # in VOlts

# Connect and configure the instrument
sourcemeter = Keithley2400("GPIB::24")
sourcemeter.reset()
sourcemeter.use_front_terminals()
sourcemeter.apply_current(current_range, compliance_voltage)
sourcemeter.measure_voltage(measure_nplc, voltage_range)
sleep(0.1)  # wait here to give the instrument time to react
sourcemeter.stop_buffer()
sourcemeter.disable_buffer()

# Allocate arrays to store the measurement results
currents = np.linspace(min_current, max_current, num=data_points)
voltages = np.zeros_like(currents)
voltage_stds = np.zeros_like(currents)

sourcemeter.enable_source()

# Loop through each current point, measure and record the voltage
for i in range(data_points):
    sourcemeter.config_buffer(averages)
    sourcemeter.source_current = currents[i]
    sourcemeter.start_buffer()
    sourcemeter.wait_for_buffer()
    # Record the average and standard deviation
    voltages[i] = sourcemeter.means[0]
    sleep(1.0)
    voltage_stds[i] = sourcemeter.standard_devs[0]

# Save the data columns in a CSV file
data = pd.DataFrame({
    'Current (A)': currents,
    'Voltage (V)': voltages,
    'Voltage Std (V)': voltage_stds,
})
data.to_csv('example.csv')

sourcemeter.shutdown()

```

When run, this example script performs the measurement and writes the data to a CSV file. That can be enough for simple work, but it also exposes several problems that PyMeasure is designed to address. In the plain-script version, the main drawbacks are:

-

Measurement progress is difficult to observe

-

Saved data does not carry its input-parameter context

-

The run does not display a live plot, and this example does not plot afterward either

-

Data is written only after a clean finish, so interrupted runs lose the output

-

Canceling an active measurement can leave the system state undefined

-

Exceptions can likewise leave the system state undefined

The [`Procedure`](https://pymeasure.readthedocs.io/en/latest/api/experiment/procedure.html#pymeasure.experiment.procedure.Procedure) class addresses these limitations. The following section introduces the [`Procedure`](https://pymeasure.readthedocs.io/en/latest/api/experiment/procedure.html#pymeasure.experiment.procedure.Procedure) class and adapts the script example so it can use that interface and its supporting features.

### Using Procedures

A Procedure object packages an experiment's ordered actions together with the parameters needed to run them correctly. Because PyMeasure tools can rely on that shared interface, this compact structure enables several useful measurement workflows.

Start with a minimal Procedure that iterates a requested number of times. Define SimpleProcedure as a subclass of Procedure because SimpleProcedure *is a* Procedure.

```python
from time import sleep
from pymeasure.experiment import Procedure
from pymeasure.experiment import IntegerParameter

class SimpleProcedure(Procedure):

    # a Parameter that defines the number of loop iterations
    iterations = IntegerParameter('Loop Iterations')

    # a list defining the order and appearance of columns in our data file
    DATA_COLUMNS = ['Iteration']

    def execute(self):
        """Execute the procedure.

        Loops over each iteration and emits the current iteration,
        before waiting for 0.01 sec, and then checking if the procedure
        should stop.
        """
        for i in range(self.iterations):
            self.emit('results', {'Iteration': i})
            sleep(0.01)
            if self.should_stop():
                break

```

At the beginning of the SimpleProcedure class, declare the required Parameters. Here, `iterations` is an IntegerParameter that supplies the loop count. Code inside the Procedure accesses that Parameter through the class variable holding it, `self.iterations`. PyMeasure replaces Parameters with their current values behind the scenes, so parameter values can be read directly through those attributes.

Set `DATA_COLUMNS` to the list of data columns to record. Its order becomes the file column order. In this example, the recorded value is the Iteration number for each loop iteration.

The `execute` method contains the main Procedure logic. In the example, it loops for the requested number of iterations and emits the recorded data, which is the Iteration number. Calling `emit` sends data to listeners; the first argument names the topic. When the topic is `'results'` and the emitted values match the data columns, those rows are written to the output file. The sleep call serves two purposes: it delays later statements by the supplied number of seconds, and it lets the CPU run other work during that pause. Good measurement scripts often use sleep carefully to handle instrument latency without monopolizing the CPU. After the pause, call `self.should_stop()` to check whether execution should end. Checking this flag lets the Procedure respond when the user cancels a run. If `startup` may take a long time, query `should_stop()` there as well so cancellation can happen early.

Note

Results do not have to be emitted one row at a time; batch emission is supported too. For example, a device such as an oscilloscope or a CCD may return several points from one measurement:

```python
intensities = self.ccd.capture()  # Assume this function returns a list of intensities for each pixel
pixels = np.arange(len(intensities))

for pixel, intensity in zip(pixels, intensities):
    self.emit('results', {'Pixel': pixel, 'Intensity': intensity})

```

Writing that loop can be awkward and may perform poorly for large data arrays. A better option is to emit the full data object at once:

```python
intensities = self.ccd.capture()  # Assume this function returns a list of intensities for each pixel
pixels = np.arange(len(intensities))

self.emit('batch results', {'Pixel': pixels, 'Intensity': intensities})

```

When using batch emission, set the topic to `'batch results'`.

These pieces are the minimum needed for a Procedure object. Next, create the SimpleProcedure object with 100 iterations.

```python
procedure = SimpleProcedure()
procedure.iterations = 100

```

The next step is running the procedure.

### Running Procedures

A Procedure runs through a Worker object. Worker execution happens in a separate Python thread, so other code, such as a graphical user interface, can continue alongside the measurement. The Worker also creates a Recorder object; the Recorder listens for data emitted by the Procedure on the `'results'` topic and writes those rows to a data file. The Results object is the bookkeeping layer that links the storage location, an accessible representation of the data, and the Procedure associated with those results.

First, create a Results object for the Procedure.

```python
from pymeasure.experiment import Results

data_filename = 'example.csv'
results = Results(procedure, data_filename)

```

Creating the Results object for the Procedure creates the file named by `data_filename` and saves the Procedure Parameters. Later, loading that file with `Results.load(data_filename)` reconstructs both the Procedure and Results objects. The stored Parameters remain human-readable in the file.

Now create a Worker from the Results object because Results contains the Procedure.

```python
from pymeasure.experiment import Worker

worker = Worker(results)

```

Worker publishes data and run-time status through dedicated queues. It can also publish the same information on the local network over a chosen TCP port when the optional `port` argument is supplied. TCP communication is useful when Listener objects need to receive information flexibly. Queues remain the default channel because they keep messages ordered, which is essential for accurate data storage and for reacting to measurement status in sequence.

The Worker can now be started.

```python
worker.start()

```

This call launches the Worker in a separate Python thread, letting the main program keep doing other work while it runs. For a script that should wait until the Worker is done, join the Worker back to the main thread.

```python
worker.join(timeout=3600) # wait at most 1 hr (3600 sec)

```

With the pieces in place, run SimpleProcedure from a script like this.

```python
from time import sleep
from pymeasure.experiment import Procedure, Results, Worker
from pymeasure.experiment import IntegerParameter

class SimpleProcedure(Procedure):

    # a Parameter that defines the number of loop iterations
    iterations = IntegerParameter('Loop Iterations')

    # a list defining the order and appearance of columns in our data file
    DATA_COLUMNS = ['Iteration']

    def execute(self):
        """Execute the procedure.

        Loops over each iteration and emits the current iteration,
        before waiting for 0.01 sec, and then checking if the procedure
        should stop.
        """
        for i in range(self.iterations):
            self.emit('results', {'Iteration': i})
            sleep(0.01)
            if self.should_stop():
                break

if __name__ == "__main__":
    procedure = SimpleProcedure()
    procedure.iterations = 100

    data_filename = 'example.csv'
    results = Results(procedure, data_filename)

    worker = Worker(results)
    worker.start()

    worker.join(timeout=3600) # wait at most 1 hr (3600 sec)

```

The if statement makes execution occur only when __name__ is __main__. That guard lets another file import the SimpleProcedure object without starting the run.

### Using Logs

Logs record important procedure-execution details. This section uses the Python logging module with PyMeasure to document what happened during a run and to provide diagnostic information for issues or bugs.

Now add logging to SimpleProcedure.

```python
import logging
log = logging.getLogger(__name__)
log.addHandler(logging.NullHandler())

from time import sleep
from pymeasure.log import console_log
from pymeasure.experiment import Procedure, Results, Worker
from pymeasure.experiment import IntegerParameter

class SimpleProcedure(Procedure):

    iterations = IntegerParameter('Loop Iterations')

    DATA_COLUMNS = ['Iteration']

    def execute(self):
        log.info("Starting the loop of %d iterations" % self.iterations)
        for i in range(self.iterations):
            data = {'Iteration': i}
            self.emit('results', data)
            log.debug("Emitting results: %s" % data)
            sleep(0.01)
            if self.should_stop():
                log.warning("Caught the stop flag in the procedure")
                break

if __name__ == "__main__":
    console_log(log)

    log.info("Constructing a SimpleProcedure")
    procedure = SimpleProcedure()
    procedure.iterations = 100

    data_filename = 'example.csv'
    log.info("Constructing the Results with a data file: %s" % data_filename)
    results = Results(procedure, data_filename)

    log.info("Constructing the Worker")
    worker = Worker(results)
    worker.start()
    log.info("Started the Worker")

    log.info("Joining with the worker in at most 1 hr")
    worker.join(timeout=3600) # wait at most 1 hr (3600 sec)
    log.info("Finished the measurement")

```

The example first imports the Python logging module and obtains a logger with the `__name__` argument, which scopes log messages to the current file. To collect every log message, including those from pymeasure, use the `''` argument instead. The `console_log` function is a convenient way to send log output to the console. The Python logging documentation covers logger usage in more detail.

### Storing metadata

Metadata ([`pymeasure.experiment.parameters.Metadata`](https://pymeasure.readthedocs.io/en/latest/api/experiment/parameters.html#pymeasure.experiment.parameters.Metadata)) stores measurement information, such as the actual starting time or instrument parameters, in the datafile header. Metadata objects are evaluated and written only after the `startup` method completes, so startup can query an instrument and then place those settings in the file. Metadata is almost as simple to use as a Parameter; the previous example can be extended with metadata as follows:

```python
from time import sleep, time
from pymeasure.experiment import Procedure
from pymeasure.experiment import IntegerParameter, Metadata

class SimpleProcedure(Procedure):

    # a Parameter that defines the number of loop iterations
    iterations = IntegerParameter('Loop Iterations')

    # the Metadata objects store information after the startup has ran
    starttime = Metadata('Start time', fget=time)
    custom_metadata = Metadata('Custom', default=1)

    # a list defining the order and appearance of columns in our data file
    DATA_COLUMNS = ['Iteration']

    def startup(self):
        self.custom_metadata = 20

    def execute(self):
        """ Loops over each iteration and emits the current iteration,
        before waiting for 0.01 sec, and then checking if the procedure
        should stop
        """
        for i in range(self.iterations):
            self.emit('results', {'Iteration': i})
            sleep(0.01)
            if self.should_stop():
                break

```

Like a Parameter, PyMeasure replaces Metadata with their values behind the scenes, making Metadata values straightforward to access.

A Metadata value can come from an `fget` method or be assigned manually inside the startup method. If fget is supplied, it runs after startup method. `fget` may also be a string; then the string is interpreted as the name of a Procedure class attribute, callable or not, whose value should be stored. Nested attributes are supported by separating names with a period, which is useful for recording an instrument property or method. Examples include instrument_name.attribute_name and instrument_name.subclass_name.attribute_name. In that dotted form, only the last element, such as attribute_name, may refer to a callable. If no `fget` method is supplied and no value is assigned manually, Metadata falls back to its default value when one exists. The fmt argument controls formatting for the Metadata-object value.

### Modifying our script

With the Procedure class features and execution model covered, return to the IV characteristic measurement and rewrite it with Procedures. The example below shows the revised script as a IVProcedure class.

```python
# Import necessary packages
from pymeasure.instruments.keithley import Keithley2400
from pymeasure.experiment import Procedure, Results, Worker
from pymeasure.experiment import IntegerParameter, FloatParameter
from time import sleep
import numpy as np

from pymeasure.log import log, console_log

class IVProcedure(Procedure):

    data_points = IntegerParameter('Data points', default=20)
    averages = IntegerParameter('Averages', default=8)
    max_current = FloatParameter('Maximum Current', units='A', default=0.001)
    min_current = FloatParameter('Minimum Current', units='A', default=-0.001)

    DATA_COLUMNS = ['Current (A)', 'Voltage (V)', 'Voltage Std (V)']

    def startup(self):
        log.info("Connecting and configuring the instrument")
        self.sourcemeter = Keithley2400("GPIB::24")
        self.sourcemeter.reset()
        self.sourcemeter.use_front_terminals()
        self.sourcemeter.apply_current(100e-3, 10.0)  # current_range = 100e-3, compliance_voltage = 10.0
        self.sourcemeter.measure_voltage(0.01, 1.0)  # nplc = 0.01, voltage_range = 1.0
        sleep(0.1)  # wait here to give the instrument time to react
        self.sourcemeter.stop_buffer()
        self.sourcemeter.disable_buffer()

    def execute(self):
        currents = np.linspace(
            self.min_current,
            self.max_current,
            num=self.data_points
        )
        self.sourcemeter.enable_source()
        # Loop through each current point, measure and record the voltage
        for current in currents:
            self.sourcemeter.config_buffer(IVProcedure.averages.value)
            log.info("Setting the current to %g A" % current)
            self.sourcemeter.source_current = current
            self.sourcemeter.start_buffer()
            log.info("Waiting for the buffer to fill with measurements")
            self.sourcemeter.wait_for_buffer()
            data = {
                'Current (A)': current,
                'Voltage (V)': self.sourcemeter.means[0],
                'Voltage Std (V)': self.sourcemeter.standard_devs[0]
            }
            self.emit('results', data)
            sleep(0.01)
            if self.should_stop():
                log.info("User aborted the procedure")
                break

    def shutdown(self):
        self.sourcemeter.shutdown()
        log.info("Finished measuring")

if __name__ == "__main__":
    console_log(log)

    log.info("Constructing an IVProcedure")
    procedure = IVProcedure()
    procedure.data_points = 20
    procedure.averages = 8
    procedure.max_current = -0.001
    procedure.min_current = 0.001

    data_filename = 'example.csv'
    log.info("Constructing the Results with a data file: %s" % data_filename)
    results = Results(procedure, data_filename)

    log.info("Constructing the Worker")
    worker = Worker(results)
    worker.start()
    log.info("Started the Worker")

    log.info("Joining with the worker in at most 1 hr")
    worker.join(timeout=3600)  # wait at most 1 hr (3600 sec)
    log.info("Finished the measurement")

```

Parentheses in `COLUMN` entries declare the physical unit for that column. For example, `'Voltage Std (V)'` declares Volts. For a dimensionless value such as Mach number, use (1). Compound units such as (m/s) or the long form (meter/second) are accepted too. The class `Results` stores data using the declared unit; in this case the unit is Volts. A `pint.Quantity` of 500 mV, for instance, is stored as 0.5 V. Strings are converted to a Quantity first, while plain numbers such as float or int are treated as already using the correct unit. Thus 5 is stored as 5 V. If a value is incompatible, either because its unit is wrong, such as meters for a voltage column, or because the value is not numeric, a warning is logged and â€˜nanâ€™ is written to the file. When no unit is given, meaning there are no parentheses, that column is not unit-checked unless a Quantity is later provided for it. In that case, the column unit becomes the base unit of the supplied value, such as meter for a value in kilometers, and later entries in the column are unit-checked. Use columns without unit checks, meaning without parentheses, for strings or booleans as well.

You now know how to build a Procedure sub-class. The next section uses those procedures in a graphical environment with live-plotting and simple queuing for multiple experiments. Those capabilities come from the Procedure object.

## Tutorials

### Tutorials

These sections help new users get started with PyMeasure.

- [Connecting to an instrument](https://pymeasure.readthedocs.io/en/latest/tutorial/connecting.html)
  - [Using adapters](https://pymeasure.readthedocs.io/en/latest/tutorial/connecting.html#using-adapters)
  - [Modifying connection settings](https://pymeasure.readthedocs.io/en/latest/tutorial/connecting.html#modifying-connection-settings)

- [Making a measurement](https://pymeasure.readthedocs.io/en/latest/tutorial/procedure.html)
  - [Using scripts](https://pymeasure.readthedocs.io/en/latest/tutorial/procedure.html#using-scripts)
  - [Using Procedures](https://pymeasure.readthedocs.io/en/latest/tutorial/procedure.html#using-procedures)

- [Using a graphical interface](https://pymeasure.readthedocs.io/en/latest/tutorial/graphical.html)
  - [Using the Plotter](https://pymeasure.readthedocs.io/en/latest/tutorial/graphical.html#using-the-plotter)
  - [Using the ManagedWindow](https://pymeasure.readthedocs.io/en/latest/tutorial/graphical.html#using-the-managedwindow)
  - [Customising the plot options](https://pymeasure.readthedocs.io/en/latest/tutorial/graphical.html#customising-the-plot-options)
  - [Using tabular format](https://pymeasure.readthedocs.io/en/latest/tutorial/graphical.html#using-tabular-format)
  - [Defining your own ManagedWindow's widgets](https://pymeasure.readthedocs.io/en/latest/tutorial/graphical.html#defining-your-own-managedwindow-s-widgets)
  - [Using the interactive Python console](https://pymeasure.readthedocs.io/en/latest/tutorial/graphical.html#using-the-interactive-python-console)
  - [Using the sequencer](https://pymeasure.readthedocs.io/en/latest/tutorial/graphical.html#using-the-sequencer)
  - [Using the estimator widget](https://pymeasure.readthedocs.io/en/latest/tutorial/graphical.html#using-the-estimator-widget)
  - [Flexible hiding of inputs](https://pymeasure.readthedocs.io/en/latest/tutorial/graphical.html#flexible-hiding-of-inputs)
  - [Using the ManagedDockWindow](https://pymeasure.readthedocs.io/en/latest/tutorial/graphical.html#using-the-manageddockwindow)
  - [Using the ManagedConsole](https://pymeasure.readthedocs.io/en/latest/tutorial/graphical.html#using-the-managedconsole)
