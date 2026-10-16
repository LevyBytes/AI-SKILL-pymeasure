# pymeasure.display.windows.managed_window.ManagedWindow

*class *pymeasure.display.windows.managed_window.ManagedWindow(*procedure_class*, *x_axis=None*, *y_axis=None*, *linewidth=1*, *log_fmt=None*, *log_datefmt=None*, ***kwargs*)

Bases: `ManagedWindowBase`

The [`PlotWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.plot_widget.PlotWidget) class shows experiment output.

See also

Tutorial: [Using the ManagedWindow](https://pymeasure.readthedocs.io/en/latest/tutorial/graphical.html#tutorial-managedwindow)

Tutorial plus example covering basic `ManagedWindow` configuration and use.

Parameters:

- **procedure_class** - experiment-describing procedure class; see [`Procedure`](https://pymeasure.readthedocs.io/en/latest/api/experiment/procedure.html#pymeasure.experiment.procedure.Procedure).

- **x_axis** - initial plot x-axis data-column (default: `None`).

- **y_axis** - initial plot y-axis data-column (default: `None`).

- **linewidth** - width used for displayed curves; the default value is 1 (default: `1`).

- **log_fmt** - log-widget formatting string (default: `None`).

- **log_datefmt** - date-format string applied in the log-widget (default: `None`).

- ****kwargs** - extra keyword arguments forwarded to `ManagedWindowBase`.
