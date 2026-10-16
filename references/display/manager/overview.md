# pymeasure.display.manager.Manager

*class *pymeasure.display.manager.Manager(*widget_list*, *browser*, *port=5888*, *log_level=20*, *parent=None*)

Bases: `BaseManager`

Executes `Experiment` classes through a queue that can add, remove, run, and abort Experiments. At creation time, the Manager connects to a [`Browser`](https://pymeasure.readthedocs.io/en/latest/api/display/browser.html#pymeasure.display.browser.Browser) plus a PyQtGraph PlotItem in the user interface; both update to reflect the Experiments execution state.
