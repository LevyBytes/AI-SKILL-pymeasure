# pymeasure.display.browser.Browser

*class *pymeasure.display.browser.Browser(*procedure_class*, *display_parameters*, *measured_quantities*, *sort_by_filename=False*, *parent=None*)

Bases: `QTreeWidget`

Graphical list view for [`Experiment`](https://pymeasure.readthedocs.io/en/latest/api/display/manager.html#pymeasure.display.manager.Experiment) objects. It lets the user inspect queued Experiments, see their status, and load or display data from earlier runs.

For different Experiments to appear in the same Browser, their DATA_COLUMNS entries must match the Browser measured_quantities.
