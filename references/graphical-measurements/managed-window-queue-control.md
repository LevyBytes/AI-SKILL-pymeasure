# ManagedWindow queue, abort/resume and plot-linewidth behavior

[ManagedWindow complete Procedure and MainWindow example](managed-window-example.md)

The graphical interface produced by that code is shown below.

 (Figure: ManagedWindow Example)

Within this code, `MainWindow` inherits from [`ManagedWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindow). Its constructor is overridden so the procedure class and related options can be supplied. The `inputs` value contains `Parameters` class-variable names; those names become graphical input fields. For long input lists, pass the boolean key-word argument `inputs_in_scrollarea` to place that area inside a scrollbar. The `displays` list has the same general shape as `inputs`, but it selects which parameters appear in the browser window. That browser tracks the experiments currently handled by the sequential queue.

For context only, not for basic operation: [`queue()`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindowBase.queue) defines the construction path for a [`Procedure`](https://pymeasure.readthedocs.io/en/latest/api/experiment/procedure.html#pymeasure.experiment.procedure.Procedure) object. `make_procedure()` builds a [`Procedure`](https://pymeasure.readthedocs.io/en/latest/api/experiment/procedure.html#pymeasure.experiment.procedure.Procedure) from the fields in the graphical form. At that point you may adjust the procedure before adding it to the queue. In this flow, [`Manager`](https://pymeasure.readthedocs.io/en/latest/api/display/manager.html#pymeasure.display.manager.Manager) wraps the [`Procedure`](https://pymeasure.readthedocs.io/en/latest/api/experiment/procedure.html#pymeasure.experiment.procedure.Procedure), [`Results`](https://pymeasure.readthedocs.io/en/latest/api/experiment/results.html#pymeasure.experiment.results.Results), and the related browser and live-graph objects in an [`Experiment`](https://pymeasure.readthedocs.io/en/latest/api/display/manager.html#pymeasure.display.manager.Experiment). The [`Manager`](https://pymeasure.readthedocs.io/en/latest/api/display/manager.html#pymeasure.display.manager.Manager) then receives that experiment and places it in the queue.

 (Figure: ManagedWindow Queue Example)

The Manager normally begins a measurement as soon as the associated procedure enters the queue. Pressing abort stops an experiment. Inside Procedure, call `self.should_stop` so the abort signal is detected and the measurement can exit. Without that check, the Procedure will ignore the abort event.

 (Figure: ManagedWindow Resume Example)

After aborting a measurement, press resume before the following measurement will proceed. That pause gives you a chance to make whatever adjustment required the abort.

 (Figure: ManagedWindow Running Example)

With ManagedWindow covered, you now have the core pieces needed to start measurements quickly and build a straightforward PyMeasure graphical interface.

Note

To improve performance, every graph uses a default linewidth of 1. When speed is acceptable, set linewidth to 2, or another value, for clearer traces by passing the linewidth keyword-argument to Plotter or ManagedWindow. If you want linewidth 2 while still needing stronger performance, enable OpenGL in the file's import section:

```python
import pyqtgraph as pg
pg.setConfigOption("useOpenGL", True)

```
