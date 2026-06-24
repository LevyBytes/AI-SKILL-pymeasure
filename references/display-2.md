# Widgets, Log, Curves, Browser

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Widget classes; Log classes; Curves classes; Browser classes.

## Widget classes

### Widget classes

 *class *pymeasure.display.widgets.browser_widget.BrowserWidget(**args*, *parent=None*)

Bases: `QWidget`

Widget adapter around the [`Browser`](https://pymeasure.readthedocs.io/en/latest/api/display/browser.html#pymeasure.display.browser.Browser) class.

 *class *pymeasure.display.widgets.directory_widget.DirectoryLineEdit(*parent=None*)

Bases: `QLineEdit`

Widget for selecting a directory path. It includes a completer for fast completion and provides a browse button.

 *class *pymeasure.display.widgets.estimator_widget.EstimatorThread(*get_estimates_callable*)

Bases: [`StoppableQThread`](https://pymeasure.readthedocs.io/en/latest/api/display/thread.html#pymeasure.display.thread.StoppableQThread)

 run(*self*)

 *class *pymeasure.display.widgets.estimator_widget.EstimatorWidget(*parent=None*)

Bases: `QWidget`

Widget for presenting preliminary estimates for a measurement procedure.

This widget uses the get_estimates method supplied by the [`Procedure`](https://pymeasure.readthedocs.io/en/latest/api/experiment/procedure.html#pymeasure.experiment.procedure.Procedure) class. get_estimates should produce a list of tuples, with each tuple holding two strings: one label and one estimate.

When `SequencerWidget` is present as well, the get_estimates Implementation can request two keyword arguments: sequence for the active sequencer and sequence_length for its length.

 check_get_estimates_signature()

Method for inspecting the get_estimates function signature. It determines the permitted input arguments and, when the return value fits EstimatorWidget, records how many estimates are available.

 display_estimates(*estimates*)

Method for refreshing the estimates currently displayed from the supplied set of estimates.

Parameters:

**estimates** â€“ The estimates to display, provided as a list of tuples containing (2) strings

 get_estimates()

Method that builds a procedure from the parameters currently entered and returns estimates for that parameter set.

 update_estimates()

Method for retrieving estimates and showing them. It is implemented so it can be connected to the â€˜updateâ€™-button.

 *class *pymeasure.display.widgets.fileinput_widget.FileInputWidget(*parent=None*)

Bases: `QWidget`

Widget for configuring the storage location for experiment data.

The widget is made up of a filename field (`FilenameLineEdit`), a directory field (`DirectoryLineEdit`), and a checkbox that controls whether the measurement is stored.

 *property *directory

String that sets the directory used when the file is stored.

 *property *extensions

List of file extensions this widget treats as recognized.

When the filename input field does not include an extension, the first value in this list is applied as the default value.

 *property *filename

String that controls the filename displayed in the filename input field.

 *property *filename_base

Read-only string containing the base portion of the filename used for storage.

 *property *filename_extension

String containing the extension used when the file is stored.

Can only be read.

 *property *filename_fixed

Boolean that controls whether the filename input field is frozen. If True, that field remains visible but is disabled (i.e., grayed out).

 *property *store_measurement

Boolean that determines whether the measurement is stored.

 *class *pymeasure.display.widgets.filename_widget.FilenameLineEdit(*procedure_class*, *parent=None*)

Bases: `QLineEdit`

Widget for choosing a filename. It includes a completer for quickly completing placeholders.

 *class *pymeasure.display.widgets.filename_widget.FilenameValidator(*placeholders*, *parent*)

Bases: `QValidator`

 fixup(*self*, *a0: str | None*) â†’ str

 validate(*self*, *a0: str | None*, *a1: int*)

 *class *pymeasure.display.widgets.filename_widget.PlaceholderCompleter(*placeholders*)

Bases: `QCompleter`

 splitPath(*self*, *path: str | None*) → list[str]

 *class *pymeasure.display.widgets.image_frame.ImageFrame(*x_axis*, *y_axis*, *z_axis=None*, *refresh_time=0.2*, *check_status=True*, *parent=None*)

Bases: `PlotFrame`

Extends `PlotFrame` so axis Z can be plotted with colors.

 ResultsClass

alias of [`ResultsImage`](https://pymeasure.readthedocs.io/en/latest/api/display/curves.html#pymeasure.display.curves.ResultsImage)

 *class *pymeasure.display.widgets.image_widget.ImageWidget(*name*, *columns*, *x_axis*, *y_axis*, *z_axis=None*, *refresh_time=0.2*, *check_status=True*, *parent=None*)

Bases: `TabWidget`, `QWidget`

Extends `ImageFrame` so different data columns can be selected dynamically.

 load(*curve*)

Add curve to widget

 new_curve(*results*, *color=<PyQt6.QtGui.QColor object>*, ***kwargs*)

Creates a new image

 remove(*curve*)

Remove curve from widget

 sizeHint(*self*) → QSize

 *class *pymeasure.display.widgets.inputs_widget.InputsWidget(*procedure_class*, *inputs=()*, *parent=None*, *hide_groups=True*, *inputs_in_scrollarea=False*)

Bases: `QWidget`

Widget adapter for the different [Inputs classes](https://pymeasure.readthedocs.io/en/latest/api/display/inputs.html).

 get_procedure()

Returns the current procedure

 *class *pymeasure.display.widgets.log_widget.HTMLFormatter(*fmt=None*, *datefmt=None*, *style='%'*, *validate=True*, ***, *defaults=None*)

Bases: `Formatter`

 format(*record*)

Convert the given record into text.

The recordâ€™s attribute dictionary supplies values for string formatting, producing the returned string. Before that formatting step, the formatter performs some setup: the record message is calculated with LogRecord.getMessage(); when the format requires time, detected through usesTime(), formatTime() formats the event timestamp; and any exception details are processed by formatException() before being added to the message.

 *class *pymeasure.display.widgets.log_widget.LogWidget(*name*, *parent=None*, *fmt=None*, *datefmt=None*)

Bases: `TabWidget`, `QWidget`

Widget for showing logging output in the GUI.

Include this widget in subclasses of [`ManagedWindowBase`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindowBase) as the recommended default.

 *class *pymeasure.display.widgets.plot_frame.PlotFrame(*x_axis=None*, *y_axis=None*, *refresh_time=0.2*, *check_status=True*, *parent=None*)

Bases: `QFrame`

Combines a PyQtGraph Plot with Crosshairs. The plot refreshes according to refresh_time, and its axes can be switched at runtime so the displayed data updates accordingly.

 ResultsClass

alias of [`ResultsCurve`](https://pymeasure.readthedocs.io/en/latest/api/display/curves.html#pymeasure.display.curves.ResultsCurve)

 parse_axis(*axis*)

Find the units of an axis by looking through the string.

 *class *pymeasure.display.widgets.plot_widget.PlotWidget(*name*, *columns*, *x_axis=None*, *y_axis=None*, *refresh_time=0.2*, *check_status=True*, *linewidth=1*, *parent=None*)

Bases: `TabWidget`, `QWidget`

Extends `PlotFrame` so different data columns can be selected dynamically.

 clear_widget()

Clear widget content

Behaviour depends on the widget and is presently used for preview mode.

 load(*curve*)

Add curve to widget

 new_curve(*results*, *color=<PyQt6.QtGui.QColor object>*, ***kwargs*)

Create a new curve

 preview_widget(*parent=None*)

Return a widget that can be used as a loading preview.

 remove(*curve*)

Remove curve from widget

 set_color(*curve*, *color*)

Change the curve pen color.

 sizeHint(*self*) → QSize

 *class *pymeasure.display.widgets.results_dialog.ResultsDialog(*procedure_class*, *widget_list=()*, *parent=None*)

Bases: `QFileDialog`

Widget that opens a dialog for loading an earlier experiment run. When a results file is chosen, the dialog shows a curve preview from that file.

This widget is used by the open_experiment method on the [`ManagedWindowBase`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindowBase) class.

 *class *pymeasure.display.widgets.sequencer_widget.ComboBoxDelegate(*owner*, *choices*)

Bases: `QStyledItemDelegate`

 createEditor(*self*, *parent: QWidget | None*, *option: QStyleOptionViewItem*, *index: QModelIndex*) → QWidget | None

 setEditorData(*self*, *editor: QWidget | None*, *index: QModelIndex*)

 setModelData(*self*, *editor: QWidget | None*, *model: QAbstractItemModel | None*, *index: QModelIndex*)

 updateEditorGeometry(*self*, *editor: QWidget | None*, *option: QStyleOptionViewItem*, *index: QModelIndex*)

 *class *pymeasure.display.widgets.sequencer_widget.ExpressionValidator

Bases: `QValidator`

 validate(*self*, *a0: str | None*, *a1: int*)

 *class *pymeasure.display.widgets.sequencer_widget.LineEditDelegate

Bases: `QStyledItemDelegate`

 createEditor(*self*, *parent: QWidget | None*, *option: QStyleOptionViewItem*, *index: QModelIndex*) → QWidget | None

 setEditorData(*self*, *editor: QWidget | None*, *index: QModelIndex*)

 setModelData(*self*, *editor: QWidget | None*, *model: QAbstractItemModel | None*, *index: QModelIndex*)

 updateEditorGeometry(*self*, *editor: QWidget | None*, *option: QStyleOptionViewItem*, *index: QModelIndex*)

 *class *pymeasure.display.widgets.sequencer_widget.SequenceDialog(*save=False*, *parent=None*)

Bases: `QFileDialog`

Widget that shows a dialog for loading or saving a sequence tree.

The dialog also includes a preview of the sequence tree.

Parameters:

**save** â€“ True when saving a file. Default False. (default: `False`)

 *class *pymeasure.display.widgets.sequencer_widget.SequencerTreeModel(*data*, *header=('Level', 'Parameter', 'Sequence')*, *parent=None*)

Bases: `QAbstractItemModel`

Model for sequencer data

Parameters:

-

**header** â€“ List of string values used as header data (default: `('Level', 'Parameter', 'Sequence')`)

-

**data** â€“ data attached to the model

-

**parent** â€“ A QWidget that QT will use as the owner for this Widget. (default: `None`)

 add_node(*parameter*, *parent=None*)

Insert a row into the sequencer.

 columnCount(*parent*)

Return how many columns are present in the model header.

The parent parameter is included solely to match the QAbstractItemModel signature.

 data(*index*, *role*)

Return the display data for the specified index and role.

Do not call this method directly. QTreeView calls it implicitly while determining what should be displayed in each location.

 flags(*index*)

Set the item flags for the supplied QModelIndex.

In this implementation, every index is marked as enabled and selectable.

 headerData(*section*, *orientation*, *role*)

Return header data for the specified section, orientation, and role.

Do not invoke this method directly. QTreeView invokes it implicitly to determine the content to display at each position.

 index(*row*, *col*, *parent*)

Return a QModelIndex instance for the row and column below the supplied parent. This method is not meant for direct calls; QTreeView uses it implicitly while resolving what to display in each position.

 parent(*index=None*)

Return the parent index for a supplied index. If no index is supplied, return an invalid QModelIndex.

Parameters:

**index** – QModelIndex optional. (default: `None`)

Returns:

 remove_node(*index*)

Delete a row from the sequencer.

 rowCount(*parent*)

Return how many children a given parent has.

>

When an invalid QModelIndex is given, return the child count below the root.

Parameters:

**parent** – QModelIndex

 setData(*self*, *index: QModelIndex*, *value: Any*, *role: int = Qt.EditRole*) â†’ bool

 visit_tree(*parent*)

Return a generator for iterating over every node in the tree.

 *class *pymeasure.display.widgets.sequencer_widget.SequencerTreeView(*parent=None*)

Bases: `QTreeView`

 setModel(*self*, *model: QAbstractItemModel | None*)

 *class *pymeasure.display.widgets.sequencer_widget.SequencerWidget(*inputs=None*, *sequence_file=None*, *parent=None*)

Bases: `QWidget`

Widget for creating a measurement sequence.

It supports parameter sweeps, can read a simple text file for loading a sequence, and can save sequences too.

Currently requires a queue function on [`ManagedWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindow) with a â€œprocedureâ€ argument.

Parameters:

**inputs** â€“ List of strings naming the parameters (default: `None`)

 load_sequence(***, *filename=None*)

Load a sequence from a .txt file.

Parameters:

**filename** â€“ Filename (string) for the file to load. (default: `None`)

 queue_sequence()

Read parameters from the sequence tree, apply them to procedures, and queue those procedures.

 *class *pymeasure.display.widgets.tab_widget.TabWidget(*name*, **args*, ***kwargs*)

Bases: `object`

Utility class that supplies default implementations for selected basic methods.

When creating a widget for subclasses of [`ManagedWindowBase`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindowBase), inherit from this class and implement these methods.

 clear_widget()

Clear widget content

Behaviour depends on the widget and is presently used for preview mode.

 load(*curve*)

Add curve to widget

 new_curve(**args*, ***kwargs*)

Create a new curve

 preview_widget(*parent=None*)

Return a Qt widget that can be used as a loading preview.

See also `ResultsDialog`. If the returned object is not None, it should also provide a name attribute.

 remove(*curve*)

Remove curve from widget

 set_color(*curve*, *color*)

Set color for widget

 *class *pymeasure.display.widgets.dock_widget.DockWidget(*name*, *procedure_class*, *x_axis_labels=None*, *y_axis_labels=None*, *linewidth=1*, *layout_path='./'*, *layout_filename=''*, *parent=None*)

Bases: `TabWidget`, `QWidget`

Widget containing a DockArea with as many Docks as required by the longest x_axis_labels or y_axis_labels list.

Parameters:

-

**name** – Name for the TabWidget

-

**procedure_class** â€“ procedure class that describes the experiment (see [`Procedure`](https://pymeasure.readthedocs.io/en/latest/api/experiment/procedure.html#pymeasure.experiment.procedure.Procedure))

-

**x_axis_labels** â€“ List of data column(s) used for the plot x-axis. If this list is shorter than y_axis_labels, its final item is reused until the length matches y_axis_labels. (default: `None`)

-

**y_axis_labels** â€“ List of data column(s) used for the plot y-axis. If this list is shorter than x_axis_labels, its final item is reused until the length matches x_axis_labels. (default: `None`)

-

**linewidth** â€“ line width used for plots in `PlotWidget` (default: `1`)

-

**layout_path** â€“ Directory path where dock layout state is saved. Default is â€˜./â€™ (default: `'./'`)

-

**layout_filename** â€“ Optional filename for the dock layout file. Default: *current procedure class* + â€œ_dock_layout.jsonâ€ (default: `''`)

-

**parent** â€“ Passed through to QtWidgets.QWidget. Default is None (default: `None`)

 contextMenuEvent(*self*, *a0: QContextMenuEvent | None*)

 new_curve(*results*, *color=<PyQt6.QtGui.QColor object>*, ***kwargs*)

Create a new curve

 save_dock_layout()

Save the current dock layout and plot settings. While the GUI is running, open the context menu by right-clicking in the widget area, then choose â€œSave Dock Layoutâ€.

 *class *pymeasure.display.widgets.table_widget.PandasModelBase(*column_index=None*, *results_list=[]*, *parent=None*)

Bases: `QAbstractTableModel`

This class supplies a model for managing multiple panda dataframes and presenting them as one table.

The multiple pandas dataframes are passed in as ResultTable class instances, and each one must have the same column count.

Assumptions: - Series in the dataframe are identical; this count is called k - Series length may vary; this count is called l(x), where x=1..n

The data may be arranged as follows: - By column: each series uses its own column, giving table shape: (k*n) x (max(l(x) x=1..n) - By row: columns stay fixed to the series count, giving table shape: k x (sum of l(x) x=1..n)

 columnCount(*self*, *parent: QModelIndex = QModelIndex()*) → int

 data(*self*, *index: QModelIndex*, *role: int = Qt.DisplayRole*) â†’ Any

 headerData(*section*, *orientation*, *role*)

Return header information

Override method from QAbstractTableModel

 pandas_column_count()

Return the total number of columns across the panda dataframes.

The selected dataframe display geometry determines this value.

 pandas_row_count()

Return the total number of rows across the panda dataframes.

The selected dataframe display geometry determines this value.

 rowCount(*self*, *parent: QModelIndex = QModelIndex()*) → int

 translate_to_global(*results*, *row*, *col*)

Convert coordinates from a single results object into full table coordinates.

 translate_to_local(*row*, *col*)

Convert coordinates from the full table back to a single results object.

 *class *pymeasure.display.widgets.table_widget.PandasModelByColumn(*column_index=None*, *results_list=[]*, *parent=None*)

Bases: `PandasModelBase`

 pandas_column_count()

Return the total number of columns across the panda dataframes.

The selected dataframe display geometry determines this value.

 pandas_row_count()

Return the total number of rows across the panda dataframes.

The selected dataframe display geometry determines this value.

 translate_to_global(*results*, *row*, *col*)

Convert coordinates from a single results object into full table coordinates.

 translate_to_local(*row*, *col*)

Convert coordinates from the full table back to a single results object.

 *class *pymeasure.display.widgets.table_widget.PandasModelByRow(*column_index=None*, *results_list=[]*, *parent=None*)

Bases: `PandasModelBase`

 pandas_column_count()

Return the total number of columns across the panda dataframes.

The selected dataframe display geometry determines this value.

 pandas_row_count()

Return the total number of rows across the panda dataframes.

The selected dataframe display geometry determines this value.

 translate_to_global(*results*, *row*, *col*)

Convert coordinates from a single results object into full table coordinates.

 translate_to_local(*row*, *col*)

Convert coordinates from the full table back to a single results object.

 *class *pymeasure.display.widgets.table_widget.ResultsTable(*results*, *color*, *column_index=None*, *force_reload=False*, *wdg=None*, ***kwargs*)

Bases: `QObject`

Class representing a panda dataframe

 *class *pymeasure.display.widgets.table_widget.Table(*refresh_time=0.2*, *check_status=True*, *force_reload=False*, *layout_class=<class 'pymeasure.display.widgets.table_widget.PandasModelByColumn'>*, *column_index=None*, *float_digits=6*, *parent=None*)

Bases: `QTableView`

Table-format view for [`Experiment`](https://pymeasure.readthedocs.io/en/latest/api/display/manager.html#pymeasure.display.manager.Experiment) objects.

 setModel(*self*, *model: QAbstractItemModel | None*)

 set_model(*model_class*)

Swap the current model for a new instance of model_class.

Class constructor: pymeasure.display.widgets.table_widget.TableWidget(name, columns).
Defaults include by_column=True, column_index=None, refresh_time=0.2, float_digits=6, check_status=True, and parent=None.

Bases: `TabWidget`, `QWidget`

Widget for showing experiment data as a table.

 clear_widget()

Clear widget content

Behaviour depends on the widget and is presently used for preview mode.

 load(*table*)

Add curve to widget

 new_curve(*results*, *color=<PyQt6.QtGui.QColor object>*, ***kwargs*)

Create a new curve

 preview_widget(*parent=None*)

Return a widget that can be used as a loading preview.

 remove(*table*)

Remove curve from widget

 set_color(*table*, *color*)

Change the curve pen color.

 *class *pymeasure.display.widgets.console_widget.ConsoleWidget(*name*, **args*, ***kwargs*)

Bases: `TabWidget`, `ConsoleWidget`

Show an interactive Python console inside the GUI.

Permit arbitrary Python commands to run at runtime and help debug the application.

It can be added to subclasses of [`ManagedWindowBase`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindowBase) by including it in the widget_list.

Parameters:

-

**name** â€“ Name for the widget, shown on the GUI tab.

-

**parent** – The Qt parent widget.

-

**namespace** â€“ A dictionary containing variables and modules exposed to the console. For example, `{'window': self, 'device': your_device}`.

-

**text** â€“ The welcome message initially shown in the console.

## Log classes

### Log classes

 *class *pymeasure.display.log.LogHandler

Bases: `Handler`

 *class *Emitter

Bases: `QObject`

 emit(*record*)

Perform the work needed to log the specified logging record.

Subclasses are expected to implement this version, so it raises a NotImplementedError.

## Curves classes

### Curves classes

 *class *pymeasure.display.curves.BufferCurve(***kwargs*)

Bases: `PlotDataItem`

Create a curve from a predefined buffer size and accept dynamically appended data.

 append(*x*, *y*)

Append data to the curve, with optional errors.

 prepare(*size*, *dtype=<class 'numpy.float32'>*)

Prepare the buffer from its size and data type.

 *class *pymeasure.display.curves.Crosshairs(*plot*, *pen=None*)

Bases: `QObject`

Attach crosshairs to a plot and emit a signal carrying the x and y graph coordinates.

 mouseMoved(*event=None*)

Refresh the mouse position when mouse movement occurs.

 update()

Refresh the mouse position from the plot data. For dynamic plots, this runs whenever the data changes so the x and y values stay aligned with what is displayed.

 *class *pymeasure.display.curves.ResultsCurve(*results*, *x*, *y*, *force_reload=False*, *wdg=None*, ***kwargs*)

Bases: `PlotDataItem`

Create a curve that loads dynamically from a file through the Results object. Each update can force a full data reload, which is useful when data changes throughout the file rather than only being appended.

 update_data()

Update the data by polling the results.

 *class *pymeasure.display.curves.ResultsImage(*results*, *x*, *y*, *z*, *force_reload=False*, *wdg=None*, ***kwargs*)

Bases: `ImageItem`

Create an image that loads dynamically from a file through the Results object.

 colormap(*x*)

Return the mapped color as RGBA floats from 0.0-1.0.

 find_img_index(*x*, *y*)

Find the integer image indices for the x and y data points closest to the supplied x and y data.

 round_up(*x*)

Convenience function for avoiding numpy rounds to even behavior.

## Browser classes

### Browser classes

 *class *pymeasure.display.browser.BaseBrowserItem

Bases: `object`

Base class for a browser item belonging to an experiment. BaseBrowerItem defines the core behavior used to show experiment progress to the user.

 *class *pymeasure.display.browser.Browser(*procedure_class*, *display_parameters*, *measured_quantities*, *sort_by_filename=False*, *parent=None*)

Bases: `QTreeWidget`

Graphical list view for [`Experiment`](https://pymeasure.readthedocs.io/en/latest/api/display/manager.html#pymeasure.display.manager.Experiment) objects. It lets the user inspect queued Experiments, see their status, and load or display data from earlier runs.

For different Experiments to appear in the same Browser, their DATA_COLUMNS entries must match the Browser measured_quantities.

 add(*experiment*)

Add an [`Experiment`](https://pymeasure.readthedocs.io/en/latest/api/display/manager.html#pymeasure.display.manager.Experiment) object to the Browser. The function verifies that the Experiment measures the required quantities before adding a BrowserItem to the Browser and filling the applicable columns with Parameter data.

 *class *pymeasure.display.browser.BrowserItem(*results*, *color*, *parent=None*)

Bases: `QTreeWidgetItem`, `BaseBrowserItem`

Represent one row in the `Browser` tree widget.
