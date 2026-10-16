# pymeasure.display.widgets.dock_widget.DockWidget

*class *pymeasure.display.widgets.dock_widget.DockWidget(*name*, *procedure_class*, *x_axis_labels=None*, *y_axis_labels=None*, *linewidth=1*, *layout_path='./'*, *layout_filename=''*, *parent=None*)

Bases: `TabWidget`, `QWidget`

Widget containing a DockArea with as many Docks as required by the longest x_axis_labels or y_axis_labels list.

Parameters:

- **name** – Name for the TabWidget

- **procedure_class** – procedure class that describes the experiment (see [`Procedure`](https://pymeasure.readthedocs.io/en/latest/api/experiment/procedure.html#pymeasure.experiment.procedure.Procedure))

- **x_axis_labels** – List of data column(s) used for the plot x-axis. If this list is shorter than y_axis_labels, its final item is reused until the length matches y_axis_labels. (default: `None`)

- **y_axis_labels** – List of data column(s) used for the plot y-axis. If this list is shorter than x_axis_labels, its final item is reused until the length matches x_axis_labels. (default: `None`)

- **linewidth** – line width used for plots in `PlotWidget` (default: `1`)

- **layout_path** – Directory path where dock layout state is saved. Default is ‘./’ (default: `'./'`)

- **layout_filename** – Optional filename for the dock layout file. Default: *current procedure class* + “_dock_layout.json” (default: `''`)

- **parent** – Passed through to QtWidgets.QWidget. Default is None (default: `None`)
