# Using Procedures

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
