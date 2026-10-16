# ManagedConsole selection and complete console/GUI example

[ManagedConsole invocation and optional progress display](console-invocation.md)

For command-line measurements with a Procedure, [`ManagedConsole`](https://pymeasure.readthedocs.io/en/latest/api/display/console.html#pymeasure.display.console.ManagedConsole) is the simplest interface. The same [`ManagedConsole`](https://pymeasure.readthedocs.io/en/latest/api/display/console.html#pymeasure.display.console.ManagedConsole) runs an experiment using the same parameters exposed by [`ManagedWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindow), but those parameters are supplied through command line switches.

It is possible to write a test that chooses either [`ManagedConsole`](https://pymeasure.readthedocs.io/en/latest/api/display/console.html#pymeasure.display.console.ManagedConsole) or [`ManagedWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindow) based on the user command line selection.

Console mode can be enabled with little setup; the example below shows the pattern.

The next example adapts the Using the ManagedWindow code and highlights the relevant sections:

1. Line 8 now imports [`ManagedConsole`](https://pymeasure.readthedocs.io/en/latest/api/display/console.html#pymeasure.display.console.ManagedConsole).

2. Line 73, adds console mode support.

```python
import sys
import random
import tempfile
from time import sleep

from pymeasure.experiment import Procedure, IntegerParameter, Parameter, FloatParameter
from pymeasure.experiment import Results
from pymeasure.display.console import ManagedConsole
from pymeasure.display.Qt import QtWidgets
from pymeasure.display.windows import ManagedWindow
import logging

log = logging.getLogger('')
log.addHandler(logging.NullHandler())

class TestProcedure(Procedure):
    iterations = IntegerParameter('Loop Iterations', default=100)
    delay = FloatParameter('Delay Time', units='s', default=0.2)
    seed = Parameter('Random Seed', default='12345')

    DATA_COLUMNS = ['Iteration', 'Random Number']

    def startup(self):
        log.info("Setting up random number generator")
        random.seed(self.seed)

    def execute(self):
        log.info("Starting to generate numbers")
        for i in range(self.iterations):
            data = {
                'Iteration': i,
                'Random Number': random.random()
            }
            log.debug("Produced numbers: %s" % data)
            self.emit('results', data)
            self.emit('progress', 100 * (i + 1) / self.iterations)
            sleep(self.delay)
            if self.should_stop():
                log.warning("Catch stop command in procedure")
                break

    def shutdown(self):
        log.info("Finished")

class MainWindow(ManagedWindow):

    def __init__(self):
        super(MainWindow, self).__init__(
            procedure_class=TestProcedure,
            inputs=['iterations', 'delay', 'seed'],
            displays=['iterations', 'delay', 'seed'],
            x_axis='Iteration',
            y_axis='Random Number'
        )
        self.setWindowTitle('GUI Example')

if __name__ == "__main__":
    if len(sys.argv) > 1:
        # If any parameter is passed, the console mode is run
        # This criteria can be changed at user discretion
        app = ManagedConsole(procedure_class=TestProcedure)
    else:
        app = QtWidgets.QApplication(sys.argv)
        window = MainWindow()
        window.show()

    sys.exit(app.exec())

```
