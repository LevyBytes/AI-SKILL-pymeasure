# Windows

> Pymeasure reference. Original prose; identifiers preserved verbatim.

### Windows classes

 *class *pymeasure.display.windows.managed_image_window.ManagedImageWindow(*procedure_class*, *x_axis*, *y_axis*, *z_axis=None*, ***kwargs*)

Bases: `ManagedWindow`

The [`ImageWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.image_widget.ImageWidget) class shows experiment output.

Parameters:

-

**procedure_class** - experiment-describing procedure class; see [`Procedure`](https://pymeasure.readthedocs.io/en/latest/api/experiment/procedure.html#pymeasure.experiment.procedure.Procedure).

-

**x_axis** - plot x-axis data-column; for the image-plot, it cannot be changed later.

-

**y_axis** - plot y-axis data-column; for the image-plot, it cannot be changed later.

-

**z_axis** - initial plot z-axis data-column; it remains changeable later (default: `None`).

-

****kwargs** - extra keyword arguments forwarded to `ManagedWindow`.

 *class *pymeasure.display.windows.managed_window.ManagedWindow(*procedure_class*, *x_axis=None*, *y_axis=None*, *linewidth=1*, *log_fmt=None*, *log_datefmt=None*, ***kwargs*)

Bases: `ManagedWindowBase`

The [`PlotWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.plot_widget.PlotWidget) class shows experiment output.

See also

Tutorial: [Using the ManagedWindow](https://pymeasure.readthedocs.io/en/latest/tutorial/graphical.html#tutorial-managedwindow)

Tutorial plus example covering basic `ManagedWindow` configuration and use.

Parameters:

-

**procedure_class** - experiment-describing procedure class; see [`Procedure`](https://pymeasure.readthedocs.io/en/latest/api/experiment/procedure.html#pymeasure.experiment.procedure.Procedure).

-

**x_axis** - initial plot x-axis data-column (default: `None`).

-

**y_axis** - initial plot y-axis data-column (default: `None`).

-

**linewidth** - width used for displayed curves; the default value is 1 (default: `1`).

-

**log_fmt** - log-widget formatting string (default: `None`).

-

**log_datefmt** - date-format string applied in the log-widget (default: `None`).

-

****kwargs** - extra keyword arguments forwarded to `ManagedWindowBase`.

 Class constructor: *pymeasure.display.windows.managed_window.ManagedWindowBase* accepts *procedure_class*, *widget_list=()*, *inputs=()*, *displays=()*, *log_channel=''*, and *log_level=20*. It also accepts *parent=None*, *sequencer=False*, *sequencer_inputs=None*, *sequence_file=None*, *inputs_in_scrollarea=False*, *enable_file_input=True*, and *hide_groups=True*.

Bases: `QMainWindow`

Base class for managing GUI experiments.

ManagedWindowBase supplies the UI for entering experiment parameters, executing multiple experiments ([`Procedure`](https://pymeasure.readthedocs.io/en/latest/api/experiment/procedure.html#pymeasure.experiment.procedure.Procedure)), plotting result curves, and showing the experiments run within one session.

ManagedWindowBase relies on a Manager to direct Workers in a Queue and exposes a simple interface; child classes must override `queue()`.

ManagedWindowBase lets the user provide widgets that present experiment information, including plots, table views, logging information, and similar displays.

Do not use this class directly; subclass it and provide an appropriate widget list. Classes that can appear as widget-list elements include:

-

[`LogWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.log_widget.LogWidget)

-

[`PlotWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.plot_widget.PlotWidget)

-

[`ImageWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.image_widget.ImageWidget)

Users may also create their own widgets, provided each one inherits from [`TabWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.tab_widget.TabWidget).

Ready-to-use classes that inherit from ManagedWindowBase include:

-

`ManagedWindow`

-

`ManagedImageWindow`

See also

Tutorial: [Using the ManagedWindow](https://pymeasure.readthedocs.io/en/latest/tutorial/graphical.html#tutorial-managedwindow)

Tutorial plus example covering basic `ManagedWindow` configuration and use.

Parameters for `__init__` constructor.

Parameters:

-

**procedure_class** - experiment-describing procedure class; see [`Procedure`](https://pymeasure.readthedocs.io/en/latest/api/experiment/procedure.html#pymeasure.experiment.procedure.Procedure).

-

**widget_list** - widgets shown in the GUI, supplied as a list (default: `()`).

-

**inputs** - list of [`Parameter`](https://pymeasure.readthedocs.io/en/latest/api/experiment/parameters.html#pymeasure.experiment.parameters.Parameter) instance variable names for which the display creates graphical fields (default: `()`).

-

**displays** - list of [`Parameter`](https://pymeasure.readthedocs.io/en/latest/api/experiment/parameters.html#pymeasure.experiment.parameters.Parameter) instance variable names shown in the browser window (default: `()`).

-

**log_channel** - `logging.Logger` instance used for logging output (default: `''`).

-

**log_level** – logging level (default: `20`)

-

**parent** - parent widget, or `None` (default: `None`).

-

**sequencer** - boolean indicating whether the sequencer must be included in the window (default: `False`).

-

**sequencer_inputs** - `None` or a list naming the parameters to scan over. Without an explicit parameter list, the parameters shown in the manager queue are used (default: `None`).

-

**sequence_file** - simple text file loaded quickly as a predefined sequence through the `Load sequence` button (default: `None`).

-

**inputs_in_scrollarea** - boolean that shows or hides a scrollbar for the input area (default: `False`).

-

**enable_file_input** - boolean that decides whether a [`FileInputWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.fileinput_widget.FileInputWidget) is displayed for choosing where experiment results are saved: True displays it (default), False does not. The widget includes a filename-base field, with or without extension; when the extension is missing it is appended. That field also accepts placeholders using parameter values and metadata values in the filename. It also includes a directory chooser for the storage location and a toggle that selects whether data is saved to the chosen file or, instead, to a temporary file (default: `True`).

-

**hide_groups** - boolean selecting how unmet parameter group conditions are handled: True, the default, hides the groups; False disables and grays them out (default: `True`).

 open_file_externally(*filename*)

Opens the datafile in an external editor or viewer. By default it uses the file type's default application, but a child class can override it to choose a different application.

 queue(*procedure=None*)

Queues a measurement using the parameters currently in the input-widget.

Semi-abstract method. Child classes must override it when filename- and directory-inputs are disabled. If those inputs remain enabled, overriding is optional and may support custom naming, input processing, or other features.

Implementations must pass an `experiment` ([`Experiment`](https://pymeasure.readthedocs.io/en/latest/api/experiment/experiment.html#pymeasure.experiment.experiment.Experiment)) object to `self.manager.queue(experiment)`; that object contains the [`Results`](https://pymeasure.readthedocs.io/en/latest/api/experiment/results.html#pymeasure.experiment.results.Results) and [`Procedure`](https://pymeasure.readthedocs.io/en/latest/api/experiment/procedure.html#pymeasure.experiment.procedure.Procedure) that will run.

A basic implementation does not need the optional procedure argument; it is required when using [`SequencerWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.sequencer_widget.SequencerWidget).

For example:

```python
def queue(self):
    filename = unique_filename('results', prefix="data") # from pymeasure.experiment

    procedure = self.make_procedure() # Procedure class was passed at construction
    results = Results(procedure, filename)
    experiment = self.new_experiment(results)

    self.manager.queue(experiment)

```

 reveal_in_file_explorer(*filename*)

Opens the file explorer at the supplied filename's location.

Return type:

`None`

Args:

filename (str): File path that should be revealed in the file explorer.

 save_experiment_copy(*source_filename*)

Saves a datafile copy to the chosen folder and file. This is mainly useful when experiments are stored in a temporary file.

 set_parameters(*parameters*)

Child classes should overwrite this method. The parameters argument is a dictionary containing Parameter objects. Parameters should replace the GUI values, allowing a user to click "Queue" and capture the same parameters.

 *class *pymeasure.display.windows.plotter_window.PlotterWindow(*plotter*, *refresh_time=0.1*, *linewidth=1*, *parent=None*)

Bases: `QMainWindow`

Window for plotting experiment results. Instantiate it through [`Plotter`](https://pymeasure.readthedocs.io/en/latest/api/display/plotter.html#pymeasure.display.plotter.Plotter), not directly.

See also

Tutorial: [Using the Plotter](https://pymeasure.readthedocs.io/en/latest/tutorial/graphical.html#tutorial-plotterwindow). Includes tutorial material and example code for `Plotter` and `PlotterWindow`.

 check_stop()

Checks whether the Plotter should stop, and if it should, exits the Qt main loop.

 *class *pymeasure.display.windows.managed_dock_window.ManagedDockWindow(*procedure_class*, *x_axis=None*, *y_axis=None*, *linewidth=1*, *log_fmt=None*, *log_datefmt=None*, ***kwargs*)

Bases: `ManagedWindowBase`

Use multiple docking windows with the [`DockWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.dock_widget.DockWidget) class to display experiment output.

Parameters:

-

**procedure_class** - experiment-describing procedure class; see [`Procedure`](https://pymeasure.readthedocs.io/en/latest/api/experiment/procedure.html#pymeasure.experiment.procedure.Procedure).

-

**x_axis** - plot x-axis data column or columns. It can be a string or a list of strings drawn from the procedure's data columns. The list length sets the plot count (default: `None`).

-

**y_axis** - plot y-axis data column or columns. It can be a string or a list of strings drawn from the procedure's data columns. The list length sets the plot count (default: `None`).

-

**linewidth** - width used for displayed curves; the default value is 1 (default: `1`).

-

**log_fmt** - log-widget formatting string (default: `None`).

-

**log_datefmt** - date-format string applied in the log-widget (default: `None`).

-

****kwargs** - extra keyword arguments forwarded to `ManagedWindowBase`.
