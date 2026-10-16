# pymeasure.display.widgets.results_dialog.ResultsDialog

*class *pymeasure.display.widgets.results_dialog.ResultsDialog(*procedure_class*, *widget_list=()*, *parent=None*)

Bases: `QFileDialog`

Widget that opens a dialog for loading an earlier experiment run. When a results file is chosen, the dialog shows a curve preview from that file.

This widget is used by the open_experiment method on the [`ManagedWindowBase`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindowBase) class.
