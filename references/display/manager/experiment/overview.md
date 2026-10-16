# pymeasure.display.manager.Experiment

*class *pymeasure.display.manager.Experiment(*results*, *curve_list=None*, *browser_item=None*, *parent=None*)

Bases: `QObject`

The Experiment class collects the [`Procedure`](https://pymeasure.readthedocs.io/en/latest/api/experiment/procedure.html#pymeasure.experiment.procedure.Procedure), [`Results`](https://pymeasure.readthedocs.io/en/latest/api/experiment/results.html#pymeasure.experiment.results.Results), and related display behavior in one object. It serves as a convenience container only.

Parameters:

- **results** – [`Results`](https://pymeasure.readthedocs.io/en/latest/api/experiment/results.html#pymeasure.experiment.results.Results) object

- **curve_list** – list of [`ResultsCurve`](https://pymeasure.readthedocs.io/en/latest/api/display/curves.html#pymeasure.display.curves.ResultsCurve) objects associated with an experiment. The curves can show separate views of that same experiment. .ManagedConsole displayed experiments do not require this value. (default: `None`)

- **browser_item** – [`BaseBrowserItem`](https://pymeasure.readthedocs.io/en/latest/api/display/browser.html#pymeasure.display.browser.BaseBrowserItem) based object (default: `None`)
