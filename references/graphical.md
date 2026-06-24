# Graphical (part 1)

> Pymeasure reference. Original prose; identifiers preserved verbatim.

### Using a graphical interface

A previous tutorial used an IV characteristic measurement on a sample as a small PyMeasure experiment. Adding PyMeasure's bundled graphical components turns that basic setup into a complete user interface.

### Using the Plotter

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

### Using the ManagedWindow

ManagedWindow is the easiest way to launch measurements built from your Procedure. Its main benefit is graphical entry for input parameters: the parameters automatically become form fields where users can type values. This lets a measurement be configured at run time instead of being hard-coded in a script.

ManagedWindow also supports a sequential queue for measurements. You can prepare multiple runs with different input parameters and observe them on the live-plot as they execute, which is valuable for long running measurements. Internally, the Manager tells the Worker which Procedure to execute and monitors the Worker status while it advances.

The next example revises the earlier code so it uses a ManagedWindow.

```python
import logging
log = logging.getLogger(__name__)
log.addHandler(logging.NullHandler())

import sys
import tempfile
import random
from time import sleep
from pymeasure.log import console_log
from pymeasure.display.Qt import QtWidgets
from pymeasure.display.windows import ManagedWindow
from pymeasure.experiment import Procedure, Results
from pymeasure.experiment import IntegerParameter, FloatParameter, Parameter

class RandomProcedure(Procedure):

    iterations = IntegerParameter('Loop Iterations', default=100)
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

class MainWindow(ManagedWindow):

    def __init__(self):
        super().__init__(
            procedure_class=RandomProcedure,
            inputs=['iterations', 'delay', 'seed'],
            displays=['iterations', 'delay', 'seed'],
            x_axis='Iteration',
            y_axis='Random Number'
        )
        self.setWindowTitle('GUI Example')

if __name__ == "__main__":
    app = QtWidgets.QApplication(sys.argv)
    window = MainWindow()
    window.show()
    sys.exit(app.exec())

```

The graphical interface produced by that code is shown below.

 (Figure: ManagedWindow Example)

Within this code, `MainWindow` inherits from [`ManagedWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindow). Its constructor is overridden so the procedure class and related options can be supplied. The `inputs` value contains `Parameters` class-variable names; those names become graphical input fields. For long input lists, pass the boolean key-word argument `inputs_in_scrollarea` to place that area inside a scrollbar. The `displays` list has the same general shape as `inputs`, but it selects which parameters appear in the browser window. That browser tracks the experiments currently handled by the sequential queue.

For context only, not for basic operation: [`queue()`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindowBase.queue) defines the construction path for a [`Procedure`](https://pymeasure.readthedocs.io/en/latest/api/experiment/procedure.html#pymeasure.experiment.procedure.Procedure) object. `make_procedure()` builds a [`Procedure`](https://pymeasure.readthedocs.io/en/latest/api/experiment/procedure.html#pymeasure.experiment.procedure.Procedure) from the fields in the graphical form. At that point you may adjust the procedure before adding it to the queue. In this flow, [`Manager`](https://pymeasure.readthedocs.io/en/latest/api/display/manager.html#pymeasure.display.manager.Manager) wraps the [`Procedure`](https://pymeasure.readthedocs.io/en/latest/api/experiment/procedure.html#pymeasure.experiment.procedure.Procedure), [`Results`](https://pymeasure.readthedocs.io/en/latest/api/experiment/results.html#pymeasure.experiment.results.Results), and the related browser and live-graph objects in an [`Experiment`](https://pymeasure.readthedocs.io/en/latest/api/display/manager.html#pymeasure.display.manager.Experiment). The [`Manager`](https://pymeasure.readthedocs.io/en/latest/api/display/manager.html#pymeasure.display.manager.Manager) then receives that experiment and places it in the queue.

 (Figure: ManagedWindow Queue Example)

The Manager normally begins a measurement as soon as the associated procedure enters the queue. Pressing abort stops an experiment. Inside Procedure, call `self.should_stop` so the abort signal is detected and the measurement can exit. Without that check, the Procedure will ignore the abort event.

 (Figure: ManagedWindow Resume Example)

After aborting a measurement, press resume before the following measurement will proceed. That pause gives you a chance to make whatever adjustment required the abort.

 (Figure: ManagedWindow Running Example)

With ManagedWindow covered, you now have the core pieces needed to start measurements quickly and build a straightforward PyMeasure graphical interface.

Note

To improve performance, every graph uses a default linewidth of 1. When speed is acceptable, set linewidth to 2, or another value, for clearer traces by passing the linewidth keyword-argument to Plotter or ManagedWindow. If you want linewidth 2 while still needing stronger performance, enable OpenGL in the file's import section:

```python
import pyqtgraph as pg
pg.setConfigOption("useOpenGL", True)

```

### The filename and directory input

A ManagedWindow instance includes filename and directory fields by default. These fields are part of [`FileInputWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.fileinput_widget.FileInputWidget) and determine where experiment results are saved.

 [(Figure: Filename and directory controls)](https://pymeasure.readthedocs.io/en/latest/_images/pymeasure-fileinput.png) [(Figure: Filename and directory controls with saving disabled for temporary-file storage)](https://pymeasure.readthedocs.io/en/latest/_images/pymeasure-fileinput_disabled.png) [(Figure: Filename field auto-complete)](https://pymeasure.readthedocs.io/en/latest/_images/pymeasure-fileinput_complete_filename.png) [(Figure: Directory field auto-complete)](https://pymeasure.readthedocs.io/en/latest/_images/pymeasure-fileinput_complete_directory.png)

When Save data is checked, the measurement is saved to a file. When it is unchecked, data is written to a temporary file instead.

The filename field accepts values with or without an extension. If the supplied extension is recognized, `.csv` and `.txt` by default, it is kept. For an unrecognized extension, the first available extension is chosen; by default that is `.csv`. A sequence number is also inserted immediately before the extension so each filename remains unique.

Filenames may include placeholders resolved by python's standard `format` function. Enter placeholders in the form `'{placeholder name:formatspec}'`. Accepted placeholder names come from every input parameter and from the measurement procedure metadata; the field tooltip lists the valid names. Since standard `format` handling is used, format specs work normally. For instance, `'DATA_delay{Delay Time:08.3f}s'` is rendered as `'DATA_delay0000.010s'`.

Auto-completion is available in both the filename field and the directory field. The directory field also has a right-side button that opens a folder-selection window.

After [`ManagedWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindow) initialization, you can set these defaults directly. That covers the default directory, default filename, recognized extensions, the initial Save data toggle value, and whether users may edit the filename field.

```python
 class MainWindow(ManagedWindow):

     def __init__(self):
         super().__init__(
             procedure_class=TestProcedure,
             inputs=['iterations', 'delay', 'seed'],
             displays=['iterations', 'delay', 'seed'],
             x_axis='Iteration',
             y_axis='Random Number',
         )
         self.setWindowTitle('GUI Example')

         self.filename = r'default_filename_delay{Delay Time:4f}s'   # Sets default filename
         self.directory = r'C:/Path/to/default/directory'            # Sets default directory
         self.store_measurement = False                              # Controls the 'Save data' toggle
         self.file_input.extensions = ["csv", "txt", "data"]         # Sets recognized extensions, first entry is the default extension
         self.file_input.filename_fixed = False                      # Controls whether the filename-field is frozen (but still displayed)

```

The boolean `enabled_file_input` argument on [`ManagedWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindow) init determines whether this widget appears. If enabled_file_input is `False`, the default [`queue()`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindowBase.queue) implementation supplied by [`ManagedWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindow) no longer functions. You must provide a custom replacement; the [`queue()`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindowBase.queue) method documentation includes a simple version.

### Customising the plot options

Both PlotterWindow and ManagedWindow delegate plotting to [pyqtgraph](http://www.pyqtgraph.org/). Through pyqtgraph you can adjust expected display settings such as axis ranges, default auto-ranging behavior, logarithmic and semilogarithmic axes, downsampling, grid display, FFT display, and similar options. Two common approaches are available:

1.

Right click the plot to change available options interactively. This is also a practical way to inspect the pyqtgraph option set, but the changes disappear when your program is restarted.

2.

Alternatively, configure the same settings in code through pyqtgraph's [PlotItem](http://www.pyqtgraph.org/documentation/graphicsItems/plotitem.html) API so the window opens with your chosen options already applied; details follow below.

For [`Plotter`](https://pymeasure.readthedocs.io/en/latest/api/display/plotter.html#pymeasure.display.plotter.Plotter), create a sub-class and override [`setup_plot()`](https://pymeasure.readthedocs.io/en/latest/api/display/plotter.html#pymeasure.display.plotter.Plotter.setup_plot). Plotter invokes this method while building the window. For example:

```python
class LogPlotter(Plotter):
    def setup_plot(self, plot):
        # use logarithmic x-axis (e.g. for frequency sweeps)
        plot.setLogMode(x=True)

```

For [`ManagedWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindow), plot customization is broader because specialization is done with inheritance. [`ManagedWindowBase`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindowBase) provides the base class used by [`ManagedWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindow) and [`ManagedImageWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_image_window.ManagedImageWindow), while those subclasses are the GUI-ready window classes.

### Using tabular format

Some experiments benefit from tabular data alongside a graph, or instead of one. [`ManagedWindowBase`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindowBase) can include a [`TableWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.table_widget.TableWidget) for displaying experiment data; the widget can also export to common formats such as CSV, HTML, etc. The example below customizes [`ManagedWindowBase`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindowBase) for tabular output, derives from the earlier example, and marks the changed lines.

```python
 import logging
 log = logging.getLogger(__name__)
 log.addHandler(logging.NullHandler())

 import sys
 import tempfile
 import random
 from time import sleep
 from pymeasure.log import console_log
 from pymeasure.display.Qt import QtWidgets
 from pymeasure.display.windows import ManagedWindowBase
 from pymeasure.display.widgets import TableWidget, LogWidget
 from pymeasure.experiment import Procedure, Results
 from pymeasure.experiment import IntegerParameter, FloatParameter, Parameter

 class RandomProcedure(Procedure):

     iterations = IntegerParameter('Loop Iterations', default=10)
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

 class MainWindow(ManagedWindowBase):

     def __init__(self):
         widget_list = (TableWidget("Experiment Table",
                                    RandomProcedure.DATA_COLUMNS,
                                    by_column=True,
                                    ),
                        LogWidget("Experiment Log"),
                        )
         super().__init__(
             procedure_class=RandomProcedure,
             inputs=['iterations', 'delay', 'seed'],
             displays=['iterations', 'delay', 'seed'],
             widget_list=widget_list,
         )
         logging.getLogger().addHandler(widget_list[1].handler)
         log.setLevel(self.log_level)
         log.info("ManagedWindow connected to logging")
         self.setWindowTitle('GUI Example')

 if __name__ == "__main__":
     app = QtWidgets.QApplication(sys.argv)
     window = MainWindow()
     window.show()
     sys.exit(app.exec())

```

The resulting GUI display appears below.

 (Figure: TableWidget Example)

### Defining your own ManagedWindow’s widgets

In the [`ManagedWindowBase`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindowBase) constructor, the `widget_list` parameter lets you add user-defined widgets to the GUI results display area. A user widget should inherit from [`TabWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.tab_widget.TabWidget) and may reimplement whichever methods require custom behavior. To understand the mechanism, review these built-in widgets:

-

[`LogWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.log_widget.LogWidget)

-

[`PlotWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.plot_widget.PlotWidget)

-

[`ImageWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.image_widget.ImageWidget)

-

`DockWidget`

-

[`TableWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.table_widget.TableWidget)

-

[`ConsoleWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.console_widget.ConsoleWidget)

### Using the interactive Python console

During a running application, it can be useful to inspect state or control an instrument interactively. PyMeasure supplies a [`ConsoleWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.console_widget.ConsoleWidget) that can be embedded directly inside [`ManagedWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindow).

Expose variables, instruments, and modules to the console by passing a `namespace` dictionary at initialization. Since [`ManagedWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindow) appends its default widgets, such as the plot and log, to the end of `widget_list`, a common pattern is to append [`ConsoleWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.console_widget.ConsoleWidget) manually after `super().__init__()` when you want it as the right-most tab.

```python
 from pymeasure.display.widgets.console_widget import ConsoleWidget

 class MainWindow(ManagedWindow):

     def __init__(self):
         super().__init__(
             procedure_class=RandomProcedure,
             inputs=['iterations', 'delay', 'seed'],
             displays=['iterations', 'delay', 'seed'],
             x_axis='Iteration',
             y_axis='Random Number',
         )
         self.setWindowTitle('GUI Example')

         # 1. Create the console widget and expose variables to it
         self.console_widget = ConsoleWidget(
             "Script Console",
             namespace={
                 'window': self,
                 'device': '<your_instrument>', # replace with your instrument instance
                 'np': '<numpy_module>' # replace with numpy if imported
             }
         )

         # 2. Append it manually so it appears as the last tab
         self.widget_list += (self.console_widget,)
         self.tabs.addTab(self.console_widget, self.console_widget.name)

```

### Using the sequencer

Beyond graphical parameter entry and multi-measurement execution through [`ManagedWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindow), [`SequencerWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.sequencer_widget.SequencerWidget) lets users enqueue a series of measurements while varying one, or more, parameters. The sequencer is therefore a convenient tool for scanning the measurement procedure's parameter space.
