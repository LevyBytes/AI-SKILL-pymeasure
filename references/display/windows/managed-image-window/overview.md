# pymeasure.display.windows.managed_image_window.ManagedImageWindow

*class *pymeasure.display.windows.managed_image_window.ManagedImageWindow(*procedure_class*, *x_axis*, *y_axis*, *z_axis=None*, ***kwargs*)

Bases: `ManagedWindow`

The [`ImageWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.image_widget.ImageWidget) class shows experiment output.

Parameters:

- **procedure_class** - experiment-describing procedure class; see [`Procedure`](https://pymeasure.readthedocs.io/en/latest/api/experiment/procedure.html#pymeasure.experiment.procedure.Procedure).

- **x_axis** - plot x-axis data-column; for the image-plot, it cannot be changed later.

- **y_axis** - plot y-axis data-column; for the image-plot, it cannot be changed later.

- **z_axis** - initial plot z-axis data-column; it remains changeable later (default: `None`).

- ****kwargs** - extra keyword arguments forwarded to `ManagedWindow`.
