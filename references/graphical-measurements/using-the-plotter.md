# Using the Plotter

Plotter does not include the richer conveniences of ManagedWindow, but it is the shortest path to live-plotting. Given a Results object, it refreshes the graph on a regular interval by reading the newest data from the file.

Warning

This section's example is known to cause runtime problems. One possible warning says that a QApplication was not created in the main thread, and another notes that nextEventMatchingMask should only be called from the Main Thread. Although some operating systems and python setups run it successfully, do not depend on the plotter until the issue is fixed. It is acceptable to skip ahead to Using the ManagedWindow section for a ManagedWindow-based workflow.

Expand SimpleProcedure into RandomProcedure, which emits random numbers during the loop. Instruments are omitted here so the example stays minimal.

```python
import logging
log = logging.getLogger(__name__)
log.addHandler(logging.NullHandler())

import random
from time import sleep
from pymeasure.log import console_log
from pymeasure.display import Plotter
from pymeasure.experiment import Procedure, Results, Worker
from pymeasure.experiment import IntegerParameter, FloatParameter, Parameter

class RandomProcedure(Procedure):

    iterations = IntegerParameter('Loop Iterations')
    delay = FloatParameter('Delay Time', units='s', default=0.2)
    seed = Parameter('Random Seed', default='12345')

    DATA_COLUMNS = ['Iteration', 'Random Number']

    def startup(self):
        log.info("Setting the seed of the random number generator")
        random.seed(self.seed)

    def execute(self):
        log.info("Starting the loop of %d iterations" % self.iterations)
        for i in range(self.iterations):
            data = {
                'Iteration': i,
                'Random Number': random.random()
            }
            self.emit('results', data)
            log.debug("Emitting results: %s" % data)
            self.emit('progress', 100 * i / self.iterations)
            sleep(self.delay)
            if self.should_stop():
                log.warning("Caught the stop flag in the procedure")
                break

if __name__ == "__main__":
    console_log(log)

    log.info("Constructing a RandomProcedure")
    procedure = RandomProcedure()
    procedure.iterations = 100

    data_filename = 'random.csv'
    log.info("Constructing the Results with a data file: %s" % data_filename)
    results = Results(procedure, data_filename)

    log.info("Constructing the Plotter")
    plotter = Plotter(results)
    plotter.start()
    log.info("Started the Plotter")

    log.info("Constructing the Worker")
    worker = Worker(results)
    worker.start()
    log.info("Started the Worker")

    log.info("Joining with the worker in at most 1 hr")
    worker.join(timeout=3600) # wait at most 1 hr (3600 sec)
    log.info("Finished the measurement")

```

The key change is that the Results object is used to create the Plotter.

```python
plotter = Plotter(results)
plotter.start()

```

The Plotter runs in a separate process, allowing it to use another CPU and improve performance. It opens a Qt graphical interface through pyqtgraph, where Results data can be displayed according to the columns present in the data.

 (Figure: Results Plotter Example)
