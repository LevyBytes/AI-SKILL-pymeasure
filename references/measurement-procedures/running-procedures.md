# Running Procedures

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
