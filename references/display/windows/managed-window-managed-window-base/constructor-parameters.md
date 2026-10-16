# pymeasure.display.windows.managed_window.ManagedWindowBase — ManagedWindowBase complete constructor parameters

[Owning PyMeasure class, adapter and connection contract](constructor-widgets.md) / [ManagedWindowBase constructor and subclassing/widget requirements](constructor-widgets.md)

Parameters for `__init__` constructor.

Parameters:

- **procedure_class** - experiment-describing procedure class; see [`Procedure`](https://pymeasure.readthedocs.io/en/latest/api/experiment/procedure.html#pymeasure.experiment.procedure.Procedure).

- **widget_list** - widgets shown in the GUI, supplied as a list (default: `()`).

- **inputs** - list of [`Parameter`](https://pymeasure.readthedocs.io/en/latest/api/experiment/parameters.html#pymeasure.experiment.parameters.Parameter) instance variable names for which the display creates graphical fields (default: `()`).

- **displays** - list of [`Parameter`](https://pymeasure.readthedocs.io/en/latest/api/experiment/parameters.html#pymeasure.experiment.parameters.Parameter) instance variable names shown in the browser window (default: `()`).

- **log_channel** - `logging.Logger` instance used for logging output (default: `''`).

- **log_level** – logging level (default: `20`)

- **parent** - parent widget, or `None` (default: `None`).

- **sequencer** - boolean indicating whether the sequencer must be included in the window (default: `False`).

- **sequencer_inputs** - `None` or a list naming the parameters to scan over. Without an explicit parameter list, the parameters shown in the manager queue are used (default: `None`).

- **sequence_file** - simple text file loaded quickly as a predefined sequence through the `Load sequence` button (default: `None`).

- **inputs_in_scrollarea** - boolean that shows or hides a scrollbar for the input area (default: `False`).

- **enable_file_input** - boolean that decides whether a [`FileInputWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.fileinput_widget.FileInputWidget) is displayed for choosing where experiment results are saved: True displays it (default), False does not. The widget includes a filename-base field, with or without extension; when the extension is missing it is appended. That field also accepts placeholders using parameter values and metadata values in the filename. It also includes a directory chooser for the storage location and a toggle that selects whether data is saved to the chosen file or, instead, to a temporary file (default: `True`).

- **hide_groups** - boolean selecting how unmet parameter group conditions are handled: True, the default, hides the groups; False disables and grays them out (default: `True`).
