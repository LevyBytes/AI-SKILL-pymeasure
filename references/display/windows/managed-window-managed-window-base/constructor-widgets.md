# pymeasure.display.windows.managed_window.ManagedWindowBase - ManagedWindowBase constructor and subclassing/widget requirements

[ManagedWindowBase complete constructor parameters](constructor-parameters.md)

Class constructor: *pymeasure.display.windows.managed_window.ManagedWindowBase* accepts *procedure_class*, *widget_list=()*, *inputs=()*, *displays=()*, *log_channel=''*, and *log_level=20*. It also accepts *parent=None*, *sequencer=False*, *sequencer_inputs=None*, *sequence_file=None*, *inputs_in_scrollarea=False*, *enable_file_input=True*, and *hide_groups=True*.

Bases: `QMainWindow`

Base class for managing GUI experiments.

ManagedWindowBase supplies the UI for entering experiment parameters, executing multiple experiments ([`Procedure`](https://pymeasure.readthedocs.io/en/latest/api/experiment/procedure.html#pymeasure.experiment.procedure.Procedure)), plotting result curves, and showing the experiments run within one session.

ManagedWindowBase relies on a Manager to direct Workers in a Queue and exposes a simple interface; child classes must override `queue()`.

ManagedWindowBase lets the user provide widgets that present experiment information, including plots, table views, logging information, and similar displays.

Do not use this class directly; subclass it and provide an appropriate widget list. Classes that can appear as widget-list elements include:

- [`LogWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.log_widget.LogWidget)

- [`PlotWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.plot_widget.PlotWidget)

- [`ImageWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.image_widget.ImageWidget)

Users may also create their own widgets, provided each one inherits from [`TabWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.tab_widget.TabWidget).

Ready-to-use classes that inherit from ManagedWindowBase include:

- `ManagedWindow`

- `ManagedImageWindow`

See also

Tutorial: [Using the ManagedWindow](https://pymeasure.readthedocs.io/en/latest/tutorial/graphical.html#tutorial-managedwindow)

Tutorial plus example covering basic `ManagedWindow` configuration and use.
