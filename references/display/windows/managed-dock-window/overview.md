# pymeasure.display.windows.managed_dock_window.ManagedDockWindow

*class *pymeasure.display.windows.managed_dock_window.ManagedDockWindow(*procedure_class*, *x_axis=None*, *y_axis=None*, *linewidth=1*, *log_fmt=None*, *log_datefmt=None*, ***kwargs*)

Bases: `ManagedWindowBase`

Use multiple docking windows with the [`DockWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.dock_widget.DockWidget) class to display experiment output.

Parameters:

- **procedure_class** - experiment-describing procedure class; see [`Procedure`](https://pymeasure.readthedocs.io/en/latest/api/experiment/procedure.html#pymeasure.experiment.procedure.Procedure).

- **x_axis** - plot x-axis data column or columns. It can be a string or a list of strings drawn from the procedure's data columns. The list length sets the plot count (default: `None`).

- **y_axis** - plot y-axis data column or columns. It can be a string or a list of strings drawn from the procedure's data columns. The list length sets the plot count (default: `None`).

- **linewidth** - width used for displayed curves; the default value is 1 (default: `1`).

- **log_fmt** - log-widget formatting string (default: `None`).

- **log_datefmt** - date-format string applied in the log-widget (default: `None`).

- ****kwargs** - extra keyword arguments forwarded to `ManagedWindowBase`.
