# Console, Plotter, Manager

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: pymeasure.display; Console class; Plotter class; Manager classes.

## pymeasure.display

### pymeasure.display

Reference material for the classes and methods provided by this package section.

- [Browser classes](https://pymeasure.readthedocs.io/en/latest/api/display/browser.html)
  - [`BaseBrowserItem`](https://pymeasure.readthedocs.io/en/latest/api/display/browser.html#pymeasure.display.browser.BaseBrowserItem)
  - [`Browser`](https://pymeasure.readthedocs.io/en/latest/api/display/browser.html#pymeasure.display.browser.Browser)
  - [`BrowserItem`](https://pymeasure.readthedocs.io/en/latest/api/display/browser.html#pymeasure.display.browser.BrowserItem)

- [Console class](https://pymeasure.readthedocs.io/en/latest/api/display/console.html)
  - [`ConsoleArgumentParser`](https://pymeasure.readthedocs.io/en/latest/api/display/console.html#pymeasure.display.console.ConsoleArgumentParser)
  - [`ConsoleBrowserItem`](https://pymeasure.readthedocs.io/en/latest/api/display/console.html#pymeasure.display.console.ConsoleBrowserItem)
  - [`ManagedConsole`](https://pymeasure.readthedocs.io/en/latest/api/display/console.html#pymeasure.display.console.ManagedConsole)

- [Curves classes](https://pymeasure.readthedocs.io/en/latest/api/display/curves.html)
  - [`BufferCurve`](https://pymeasure.readthedocs.io/en/latest/api/display/curves.html#pymeasure.display.curves.BufferCurve)
  - [`Crosshairs`](https://pymeasure.readthedocs.io/en/latest/api/display/curves.html#pymeasure.display.curves.Crosshairs)
  - [`ResultsCurve`](https://pymeasure.readthedocs.io/en/latest/api/display/curves.html#pymeasure.display.curves.ResultsCurve)
  - [`ResultsImage`](https://pymeasure.readthedocs.io/en/latest/api/display/curves.html#pymeasure.display.curves.ResultsImage)

- [Inputs classes](https://pymeasure.readthedocs.io/en/latest/api/display/inputs.html)
  - [`BooleanInput`](https://pymeasure.readthedocs.io/en/latest/api/display/inputs.html#pymeasure.display.inputs.BooleanInput)
  - [`Input`](https://pymeasure.readthedocs.io/en/latest/api/display/inputs.html#pymeasure.display.inputs.Input)
  - [`IntegerInput`](https://pymeasure.readthedocs.io/en/latest/api/display/inputs.html#pymeasure.display.inputs.IntegerInput)
  - [`ListInput`](https://pymeasure.readthedocs.io/en/latest/api/display/inputs.html#pymeasure.display.inputs.ListInput)
  - [`ScientificInput`](https://pymeasure.readthedocs.io/en/latest/api/display/inputs.html#pymeasure.display.inputs.ScientificInput)
  - [`StringInput`](https://pymeasure.readthedocs.io/en/latest/api/display/inputs.html#pymeasure.display.inputs.StringInput)
  - [`VectorInput`](https://pymeasure.readthedocs.io/en/latest/api/display/inputs.html#pymeasure.display.inputs.VectorInput)

- [Listeners classes](https://pymeasure.readthedocs.io/en/latest/api/display/listeners.html)
  - [`Monitor`](https://pymeasure.readthedocs.io/en/latest/api/display/listeners.html#pymeasure.display.listeners.Monitor)
  - [`QListener`](https://pymeasure.readthedocs.io/en/latest/api/display/listeners.html#pymeasure.display.listeners.QListener)

- [Log classes](https://pymeasure.readthedocs.io/en/latest/api/display/log.html)
  - [`LogHandler`](https://pymeasure.readthedocs.io/en/latest/api/display/log.html#pymeasure.display.log.LogHandler)

- [Manager classes](https://pymeasure.readthedocs.io/en/latest/api/display/manager.html)
  - [`BaseManager`](https://pymeasure.readthedocs.io/en/latest/api/display/manager.html#pymeasure.display.manager.BaseManager)
  - [`Experiment`](https://pymeasure.readthedocs.io/en/latest/api/display/manager.html#pymeasure.display.manager.Experiment)
  - [`ExperimentQueue`](https://pymeasure.readthedocs.io/en/latest/api/display/manager.html#pymeasure.display.manager.ExperimentQueue)
  - [`Manager`](https://pymeasure.readthedocs.io/en/latest/api/display/manager.html#pymeasure.display.manager.Manager)

- [Plotter class](https://pymeasure.readthedocs.io/en/latest/api/display/plotter.html)
  - [`Plotter`](https://pymeasure.readthedocs.io/en/latest/api/display/plotter.html#pymeasure.display.plotter.Plotter)

- [Qt classes](https://pymeasure.readthedocs.io/en/latest/api/display/Qt.html)
- [Thread classes](https://pymeasure.readthedocs.io/en/latest/api/display/thread.html)
  - [`StoppableQThread`](https://pymeasure.readthedocs.io/en/latest/api/display/thread.html#pymeasure.display.thread.StoppableQThread)

- [Widget classes](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html)
  - [`BrowserWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.browser_widget.BrowserWidget)
  - [`DirectoryLineEdit`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.directory_widget.DirectoryLineEdit)
  - [`EstimatorThread`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.estimator_widget.EstimatorThread)
  - [`EstimatorWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.estimator_widget.EstimatorWidget)
  - [`FileInputWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.fileinput_widget.FileInputWidget)
  - [`FilenameLineEdit`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.filename_widget.FilenameLineEdit)
  - [`FilenameValidator`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.filename_widget.FilenameValidator)
  - [`PlaceholderCompleter`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.filename_widget.PlaceholderCompleter)
  - [`ImageFrame`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.image_frame.ImageFrame)
  - [`ImageWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.image_widget.ImageWidget)
  - [`InputsWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.inputs_widget.InputsWidget)
  - [`HTMLFormatter`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.log_widget.HTMLFormatter)
  - [`LogWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.log_widget.LogWidget)
  - [`PlotFrame`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.plot_frame.PlotFrame)
  - [`PlotWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.plot_widget.PlotWidget)
  - [`ResultsDialog`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.results_dialog.ResultsDialog)
  - [`ComboBoxDelegate`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.sequencer_widget.ComboBoxDelegate)
  - [`ExpressionValidator`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.sequencer_widget.ExpressionValidator)
  - [`LineEditDelegate`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.sequencer_widget.LineEditDelegate)
  - [`SequenceDialog`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.sequencer_widget.SequenceDialog)
  - [`SequencerTreeModel`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.sequencer_widget.SequencerTreeModel)
  - [`SequencerTreeView`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.sequencer_widget.SequencerTreeView)
  - [`SequencerWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.sequencer_widget.SequencerWidget)
  - [`TabWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.tab_widget.TabWidget)
  - [`DockWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.dock_widget.DockWidget)
  - [`PandasModelBase`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.table_widget.PandasModelBase)
  - [`PandasModelByColumn`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.table_widget.PandasModelByColumn)
  - [`PandasModelByRow`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.table_widget.PandasModelByRow)
  - [`ResultsTable`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.table_widget.ResultsTable)
  - [`Table`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.table_widget.Table)
  - [`TableWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.table_widget.TableWidget)
  - [`ConsoleWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.console_widget.ConsoleWidget)

- [Windows classes](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html)
  - [`ManagedImageWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_image_window.ManagedImageWindow)
  - [`ManagedWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindow)
  - [`ManagedWindowBase`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindowBase)
  - [`PlotterWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.plotter_window.PlotterWindow)
  - [`ManagedDockWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_dock_window.ManagedDockWindow)

## Console class

### Console class

 *class *pymeasure.display.console.ConsoleArgumentParser(*procedure_class*, ***kwargs*)

Bases: `ArgumentParser`

 setup_parser()

Configure command-line argument parsing from the available parameter metadata.

 *class *pymeasure.display.console.ConsoleBrowserItem(*progress_bar*)

Bases: [`BaseBrowserItem`](https://pymeasure.readthedocs.io/en/latest/api/display/browser.html#pymeasure.display.browser.BaseBrowserItem)

 *class *pymeasure.display.console.ManagedConsole(*procedure_class*, *log_channel=''*, *log_level=20*, ***kwargs*)

Bases: `QCoreApplication`

Console-oriented foundation for managing experiments.

Parameters for `__init__` constructor.

Parameters:

-

**procedure_class** – class for the procedure that defines the experiment; see [`Procedure`](https://pymeasure.readthedocs.io/en/latest/api/experiment/procedure.html#pymeasure.experiment.procedure.Procedure).

-

**log_channel** – `logging.Logger` object used for emitted log output (default: `''`).

-

**log_level** – logging level (default: `20`)

-

**kwargs** – extra keyword arguments forwarded into the `ConsoleArgumentParser` constructor.

 abort()

Stop the active Experiment; raise an exception when no experiment is running.

 exec() → int

 get_filename(*directory*, *procedure=None*)

Get the filename used when storing the results file.

Parameters:

**directory** – folder used for the filename that is returned.

## Plotter class

### Plotter class

 *class *pymeasure.display.plotter.Plotter(*results*, *refresh_time=0.1*, *linewidth=1*)

Bases: `StoppableThread`

Plotter reads data through a Results object and updates the graph dynamically from a file.

See also

Tutorial: [Using the Plotter](https://pymeasure.readthedocs.io/en/latest/tutorial/graphical.html#tutorial-plotterwindow).

Tutorial material and an example demonstrate how to work with Plotter and PlotterWindow.

 run()

Method that defines what the thread does while it is active.

Subclasses may replace this method. The default run() implementation calls the target callable supplied to the object constructor, when one was provided, and passes positional values from args plus keyword values from kwargs.

 setup_plot(*plot*)

By default, this method has no effect. A child class can override it to configure custom plot-window behavior through its [PlotItem](https://pyqtgraph.readthedocs.io/en/latest/graphicsItems/plotitem.html).

Parameters:

**plot** – [PlotItem](https://pyqtgraph.readthedocs.io/en/latest/graphicsItems/plotitem.html) instance owned by this window.

## Manager classes

### Manager classes

 *class *pymeasure.display.manager.BaseManager(*port=5888*, *log_level=20*, *parent=None*)

Bases: `QObject`

Manages execution for `Experiment` classes with a queue that supports adding, removing, running, and aborting Experiments.

 abort()

Abort the active Experiment; if nothing is currently running, raise an exception.

 clear()

Remove all Experiments

 is_running()

Return True when a procedure is running at the time of the check.

 load(*experiment*)

Load a previously executed Experiment

 next()

Start the next queued experiment only when no other experiment is running and the queue contains a procedure.

 queue(*experiment*)

Place an experiment onto the queue.

 remove(*experiment*)

Removes an Experiment

 resume()

Resume processing of the queue.

 *class *pymeasure.display.manager.Experiment(*results*, *curve_list=None*, *browser_item=None*, *parent=None*)

Bases: `QObject`

The Experiment class collects the [`Procedure`](https://pymeasure.readthedocs.io/en/latest/api/experiment/procedure.html#pymeasure.experiment.procedure.Procedure), [`Results`](https://pymeasure.readthedocs.io/en/latest/api/experiment/results.html#pymeasure.experiment.results.Results), and related display behavior in one object. It serves as a convenience container only.

Parameters:

-

**results** – [`Results`](https://pymeasure.readthedocs.io/en/latest/api/experiment/results.html#pymeasure.experiment.results.Results) object

-

**curve_list** – list of [`ResultsCurve`](https://pymeasure.readthedocs.io/en/latest/api/display/curves.html#pymeasure.display.curves.ResultsCurve) objects associated with an experiment. The curves can show separate views of that same experiment. .ManagedConsole displayed experiments do not require this value. (default: `None`)

-

**browser_item** – [`BaseBrowserItem`](https://pymeasure.readthedocs.io/en/latest/api/display/browser.html#pymeasure.display.browser.BaseBrowserItem) based object (default: `None`)

 *class *pymeasure.display.manager.ExperimentQueue

Bases: `QObject`

Models an Experiments queue and provides convenient query operations.

 has_next()

Return True when the queue still contains another item.

 next()

Return the next experiment from the queue.

 *class *pymeasure.display.manager.Manager(*widget_list*, *browser*, *port=5888*, *log_level=20*, *parent=None*)

Bases: `BaseManager`

Executes `Experiment` classes through a queue that can add, remove, run, and abort Experiments. At creation time, the Manager connects to a [`Browser`](https://pymeasure.readthedocs.io/en/latest/api/display/browser.html#pymeasure.display.browser.Browser) plus a PyQtGraph PlotItem in the user interface; both update to reflect the Experiments execution state.

 load(*experiment*)

Load a previously executed Experiment

 remove(*experiment*)

Removes an Experiment
