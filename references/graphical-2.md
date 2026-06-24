# Graphical (part 2)

> Pymeasure reference. Original prose; identifiers preserved verbatim.

Enable the sequencer by supplying two extra keyword arguments to [`ManagedWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindow): `sequencer` and `sequencer_inputs`. Set `sequencer` to a boolean that controls whether the window includes the sequencer. For `sequencer_inputs`, pass `None` or a list containing the parameter names to scan. When that list is omitted, the manager queue display determines the parameters.

To make the sequencer usable, [`ManagedWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindow) must provide a `queue` method. That method should accept a keyword argument, preferably keyword-only for safety, named `procedure`; pass the procedure instance through that argument. The sequencer calls this method when it queues the parameter scan.

To add the sequencer to the earlier example, only [`ManagedWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindow) needs a small adjustment; the changed lines are marked below:

```python
 class MainWindow(ManagedWindow):

     def __init__(self):
         super().__init__(
             procedure_class=TestProcedure,
             inputs=['iterations', 'delay', 'seed'],
             displays=['iterations', 'delay', 'seed'],
             x_axis='Iteration',
             y_axis='Random Number',
             sequencer=True,                                      # Added line
             sequencer_inputs=['iterations', 'delay', 'seed'],    # Added line
             sequence_file="gui_sequencer_example_sequence.txt",  # Added line, optional
         )
         self.setWindowTitle('GUI Example')

```

This places the sequencer below the input panel.

 (Figure: Sequencer widget example)

The widget includes a tree-view for composing the sequence. It presents three columns: `level` (showing the nesting depth for an item), `parameter` (a drop-down menu for choosing the parameter that item sequences), and `sequence` (the text-box used to enter the sequence). The first two columns are mostly self-explanatory; the final one needs more detail.

For flexible sequence entry, the sequence is written in a text-box where the user may type any single-line expression that produces a list. Several helpers are available for that expression: from the main python library, `range`, `sorted`, and `list`; from numpy, the functions listed below. You do not need to prefix them with `numpy.` or any abbreviation. Available numpy names are `arange`, `linspace`, `arccos`, `arcsin`, `arctan`, `arctan2`, `ceil`, `cos`, `cosh`, and `degrees`; the list continues with `e`, `exp`, `fabs`, `floor`, `fmod`, `frexp`, `hypot`, `ldexp`, and `log`; it also includes `log10`, `modf`, `pi`, `power`, `radians`, `sin`, `sinh`, `sqrt`, `tan`, and `tanh`.

For example, `arange(0, 10, 1)` returns values separated by 1, while `exp(arange(0, 10, 1))` turns those values into an exponentially growing sequence. This makes more elaborate sequences practical to enter.

Use `Add root item`, `Add item`, and `Remove item` to grow or trim the sequence. The add-child control creates a child under the currently selected entry, while the remove control deletes the selected entry. Press the `Queue` sequence button to enqueue the sequence that was entered. If any sequence text-box cannot be evaluated, the logger reports the error and nothing is queued.

You can also create a sequence file so the user does not have to retype the same sequence each time. Save the sequence currently built in the GUI with `Save sequence`, or write a simple text file directly. After the file exists, load it with `Load sequence`.

Each line in the sequence file contributes one item to the sequence tree. The line begins with dashes (`-`) to encode the item level, with 1 dash meaning top level, then gives the parameter name and sequence string, both written as a python string between parentheses.

Below is an example sequence file that produces the sequence displayed in the preceding figure.

```python
- "Delay Time", "arange(0.25, 1, 0.25)"
-- "Random Seed", "[1, 4, 8]"
--- "Loop Iterations", "exp(linspace(1, 5, 3))"
-- "Random Seed", "arange(10, 100, 10)"

```

This file can be loaded automatically when the program starts by adding `sequence_file="filename.txt"` as a key-word argument in the `super().__init__` call, matching the example.

### Using the estimator widget

An [`EstimatorWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.estimator_widget.EstimatorWidget) is available for defining and calculating measurement estimates. The widget turns on automatically after `get_estimates` is added to the `Procedure`.

The smallest useful `get_estimates` implementation simply returns the estimated measurement duration in seconds, as an `int` or a `float`. In the example from the Using the ManagedWindow section, update the `Procedure` to:

```python
class RandomProcedure(Procedure):

    # ...

    def get_estimates(self, sequence_length=None, sequence=None):

        return self.iterations * self.delay

```

That change places the estimator widget in the left dock. In this configuration, duration and finishing-time for one measurement are always visible. If SequencerWidget is active as well, the full sequence length, duration, and finishing-time are shown too.

For broader estimate displays, `get_estimates` may instead return a list of tuples, for example duration, filesize, finishing-time, and other values. Each tuple contains two strings: first the estimate name (label), then the estimate value.

The example from the Using the ManagedWindow section can be adapted by changing the `Procedure` to:

```python
class RandomProcedure(Procedure):

    # ...

    def get_estimates(self, sequence_length=None, sequence=None):

        duration = self.iterations * self.delay

        estimates = [
            ("Duration", "%d s" % int(duration)),
            ("Number of lines", "%d" % int(self.iterations)),
            ("Sequence length", str(sequence_length)),
            ('Measurement finished at', str(datetime.now() + timedelta(seconds=duration))),
        ]

        return estimates

```

That version also places the estimator widget in the dock on the left.

 (Figure: Estimator widget example)

After the widget is initialized, both the estimate label and the estimate value can still be changed; however, the number of estimates is fixed.

The function implementation does not have to declare keyword arguments; they are supplied only when the signature requests them, so `def get_estimates(self)` is valid. The accepted names are `sequence`, containing the complete sequencer sequence when one exists, and `sequence_length`, an integer length for that sequence when available. Without a sequencer, or when parsing the sequence fails, both `sequence` and `sequence_length` are set to `None`.

The estimates refresh automatically every 2 seconds. The Ã¢â‚¬Å“Update continuouslyÃ¢â‚¬Â-checkbox controls that interval and has three states: off (no refresh), auto-update every 2 seconds (default), and auto-update every 100 milliseconds. When continuous updating is disabled, use the Ã¢â‚¬Å“updateÃ¢â‚¬Â-button to refresh manually.

### Flexible hiding of inputs

Some procedures need to hide or show several inputs, for instance when a measurement branch is skipped after a single `BooleanParameter` changes state. In that situation, a `Parameter` can be tied to a controlling `Parameter`; the `Input` for the controlled `Parameter` is shown or hidden according to the controlling value. Configure this relationship with the `group_by` key-word argument.

```python
toggle = BooleanParameter("toggle", default=True)
param = FloatParameter('some parameter', group_by='toggle')

```

When `toggle` and `param` are both shown in the `InputsWidget` (for example via `inputs=['iterations', 'delay', 'seed']` above), the checkbox for `toggle` controls whether the input-field of `param` is displayed. By default, a group is shown when the `group_by` `Parameter` evaluates to `True`; this default mainly matters for a `BooleanParameter`. Other matching values can be supplied through the `group_condition` keyword argument.

```python
iterations = IntegerParameter('Loop Iterations', default=100)
param = FloatParameter('some parameter', group_by='iterations', group_condition=99)

```

With this setup, the input of `param` appears only when `iterations` equals 99. Any `Parameter` type can serve as the `group_by` `Parameter`.

Further customization is available by using a (lambda)function as the condition:

```python
iterations = IntegerParameter('Loop Iterations', default=100)
param = FloatParameter('some parameter', group_by='iterations', group_condition=lambda v: 50 < v < 100)

```

Here, the input of `param` is displayed only when `iterations` has a value from 51 through 99.

Set the `ManagedWindow` keyword-argument `hide_groups` to choose the behavior: `hide_groups = True` hides grouped inputs, while `hide_groups = False` leaves them disabled / grayed-out.

You may also pass several parameters to `group_by`. In that form, the input is displayed only when every condition is true. Multiple grouping parameters can be supplied as a dict mapping strings to conditions, or as a list of parameter-name strings; for the list form, `group_condition` may be one condition or a list of conditions:

```python
iterations = IntegerParameter('Loop Iterations', default=100)
toggle = BooleanParameter('A checkbox')
param_A = FloatParameter('some parameter', group_by=['iterations', 'toggle'], group_condition=[lambda v: 50 < v < 100, True])
param_B = FloatParameter('some parameter', group_by={'iterations': lambda v: 50 < v < 100, 'toggle': True})

```

In this example, `param_A` and `param_B` use the same grouping rules: both are visible only when `iterations` is from 51 to 99 and the toggle checkbox is checked (i.e. True).

### Using the ManagedDockWindow

Starting from the Using the ManagedWindow example that uses `ManagedWindow`, you can switch to [`ManagedDockWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_dock_window.ManagedDockWindow) to create a GUI with multiple graphs. Those graphs can stay docked in the main GUI window or be popped out into separate windows.

First, apply the highlighted edits below to the Using the ManagedWindow code example:

1.

Line 10 now imports [`ManagedDockWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_dock_window.ManagedDockWindow).

2.

Line 20, along with lines 32 and 33, adds two extra recorded data columns: `'Random Number 2'` and `'Random Number 3'`.

3.

Line 44 changes `MainWindow` so it subclasses `ManagedDockWindow`.

4.

Line 51 passes a list of strings taken from `DATA_COLUMNS` into the `x_axis` argument.

5.

Line 52 passes a list of strings from `DATA_COLUMNS` into the `y_axis` argument.

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

We can now display the `ManagedDockWindow`:

 (Figure: Managed dock window)

The screenshot above shows that the example created three docks with these Ã¢â‚¬Å“X AxisÃ¢â‚¬Â and Ã¢â‚¬Å“Y AxisÃ¢â‚¬Â labels:

1.

**X Axis:** “Iteration” **Y Axis:** “Random Number 1”

2.

**X Axis:** “Random Number 1” **Y Axis:** “Random Number 2”

3.

**X Axis:** “Random Number 1” **Y Axis:** “Random Number 3”

The string lists supplied to `x_axis` and `y_axis` provide the initial labels for each dockable plot. The number of dockable plots comes from whichever list is longest. In the example, `x_axis` and `y_axis` are defined like this:

```python
x_axis=['Iteration', 'Random Number 1'],
y_axis=['Random Number 1','Random Number 2', 'Random Number 3']

```

When one list is longer, the remaining dockable plots reuse the final element of the other list as their default label. That is why this example shows two **X Axis** labels set to Ã¢â‚¬Å“Random Number 1Ã¢â‚¬Â. Between `x_axis` and `y_axis`, the longer list controls how many plots are built; here `y_axis` is longest, with a length of three, so three plots are created.

To detach a dockable plot into a separate window, double-click the blue Ã¢â‚¬Å“Dock #Ã¢â‚¬Â title bar, which appears on the left side of each plot by default:

 (Figure: Managed dock window pop-up)

Close the popped-out window with the X icon in the top-right corner to return it to the main window.

Once the docks are arranged, save the layout by right-clicking a dock widget and choosing Ã¢â‚¬Å“Save Dock LayoutÃ¢â‚¬Â from the context menu. This writes one file containing every dock layout plus each plot setting. The default location is the current working directory of the python file that launched `ManagedDockWindow`. The default file name is Ã¢â‚¬Ëœ*procedure class* + Ã¢â‚¬Å“_dock_layout.jsonÃ¢â‚¬ÂÃ¢â‚¬â„¢; in this example it becomes Ã¢â‚¬Å“./RandomProcedure_dock_layout.jsonÃ¢â‚¬Â.

On the next run of the python file that calls `ManagedDockWindow`, the layout file is detected and loaded when it is present.

 (Figure: Save dock window layout)

Dockable plots can be rearranged relative to one another by dragging within the main dock window. Drag the blue â€œDock #â€ title bar to the left or right edge of another plot to place the two plots side by side:

 (Figure: Side drag managed dock window) (Figure: Side position managed dock window)

Dragging the blue â€œDock #â€ title bar to the top or bottom edge of another plot changes the vertical ordering of the plots:

 (Figure: Top position managed dock window)

Dragging the blue Ã¢â‚¬Å“Dock #Ã¢â‚¬Â title bar onto the middle of another plot groups the two plots into a tabbed view:

 (Figure: Tab drag managed dock window) (Figure: Tab position managed dock window)

### Using the ManagedConsole

For command-line measurements with a Procedure, [`ManagedConsole`](https://pymeasure.readthedocs.io/en/latest/api/display/console.html#pymeasure.display.console.ManagedConsole) is the simplest interface. The same [`ManagedConsole`](https://pymeasure.readthedocs.io/en/latest/api/display/console.html#pymeasure.display.console.ManagedConsole) runs an experiment using the same parameters exposed by [`ManagedWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindow), but those parameters are supplied through command line switches.

It is possible to write a test that chooses either [`ManagedConsole`](https://pymeasure.readthedocs.io/en/latest/api/display/console.html#pymeasure.display.console.ManagedConsole) or [`ManagedWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindow) based on the user command line selection.

Console mode can be enabled with little setup; the example below shows the pattern.

The next example adapts the Using the ManagedWindow code and highlights the relevant sections:

1.

Line 8 now imports [`ManagedConsole`](https://pymeasure.readthedocs.io/en/latest/api/display/console.html#pymeasure.display.console.ManagedConsole).

2.

Line 73, adds console mode support.

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

If the script above is run with no parameter, it opens the graphical user interface example. Running it as shown below uses command line mode:

```bash
python console.py --iterations 10 --result-file console_test

```

Console output looks like this; to display the progress bar, install the optional module [progressbar2](https://pypi.org/project/progressbar2/):

 (Figure: Console mode output)

### Other useful commands

Use this to display every command line switch:

```bash
python console.py --help

```

Use this command to run an experiment with parameters loaded from an existing result file.

```bash
python console.py --use-result-file console_test2023-08-09_1.csv

```
