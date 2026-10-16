# ManagedDockWindow setup changes and complete example

[ManagedDockWindow axes, floating docks, layout persistence and tabs](dock-layout-and-axes.md)

Starting from the Using the ManagedWindow example that uses `ManagedWindow`, you can switch to [`ManagedDockWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_dock_window.ManagedDockWindow) to create a GUI with multiple graphs. Those graphs can stay docked in the main GUI window or be popped out into separate windows.

First, apply the highlighted edits below to the Using the ManagedWindow code example:

1. Line 10 now imports [`ManagedDockWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_dock_window.ManagedDockWindow).

2. Line 20, along with lines 32 and 33, adds two extra recorded data columns: `'Random Number 2'` and `'Random Number 3'`.

3. Line 44 changes `MainWindow` so it subclasses `ManagedDockWindow`.

4. Line 51 passes a list of strings taken from `DATA_COLUMNS` into the `x_axis` argument.

5. Line 52 passes a list of strings from `DATA_COLUMNS` into the `y_axis` argument.

```python
import logging
log = logging.getLogger(__name__)
log.addHandler(logging.NullHandler())

import sys
import tempfile
import random
from time import sleep
from pymeasure.display.Qt import QtWidgets
from pymeasure.display.windows.managed_dock_window import ManagedDockWindow
from pymeasure.experiment import Procedure, Results
from pymeasure.experiment import IntegerParameter, FloatParameter, Parameter

class RandomProcedure(Procedure):

    iterations = IntegerParameter('Loop Iterations', default=10)
    delay = FloatParameter('Delay Time', units='s', default=0.2)
    seed = Parameter('Random Seed', default='12345')

    DATA_COLUMNS = ['Iteration', 'Random Number 1', 'Random Number 2', 'Random Number 3']

    def startup(self):
        log.info("Setting the seed of the random number generator")
        random.seed(self.seed)

    def execute(self):
        log.info("Starting the loop of %d iterations" % self.iterations)
        for i in range(self.iterations):
            data = {
                'Iteration': i,
                'Random Number 1': random.random(),
                'Random Number 2': random.random(),
                'Random Number 3': random.random()
            }
            self.emit('results', data)
            log.debug("Emitting results: %s" % data)
            self.emit('progress', 100 * i / self.iterations)
            sleep(self.delay)
            if self.should_stop():
                log.warning("Caught the stop flag in the procedure")
                break

class MainWindow(ManagedDockWindow):

    def __init__(self):
        super().__init__(
            procedure_class=RandomProcedure,
            inputs=['iterations', 'delay', 'seed'],
            displays=['iterations', 'delay', 'seed'],
            x_axis=['Iteration', 'Random Number 1'],
            y_axis=['Random Number 1','Random Number 2', 'Random Number 3']
        )
        self.setWindowTitle('GUI Example')

if __name__ == "__main__":
    app = QtWidgets.QApplication(sys.argv)
    window = MainWindow()
    window.show()
    sys.exit(app.exec())

```
