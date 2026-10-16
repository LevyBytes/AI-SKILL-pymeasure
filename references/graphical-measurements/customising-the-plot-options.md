# Customising the plot options

Both PlotterWindow and ManagedWindow delegate plotting to [pyqtgraph](http://www.pyqtgraph.org/). Through pyqtgraph you can adjust expected display settings such as axis ranges, default auto-ranging behavior, logarithmic and semilogarithmic axes, downsampling, grid display, FFT display, and similar options. Two common approaches are available:

1. Right click the plot to change available options interactively. This is also a practical way to inspect the pyqtgraph option set, but the changes disappear when your program is restarted.

2. Alternatively, configure the same settings in code through pyqtgraph's [PlotItem](http://www.pyqtgraph.org/documentation/graphicsItems/plotitem.html) API so the window opens with your chosen options already applied; details follow below.

For [`Plotter`](https://pymeasure.readthedocs.io/en/latest/api/display/plotter.html#pymeasure.display.plotter.Plotter), create a sub-class and override [`setup_plot()`](https://pymeasure.readthedocs.io/en/latest/api/display/plotter.html#pymeasure.display.plotter.Plotter.setup_plot). Plotter invokes this method while building the window. For example:

```python
from pymeasure.display.plotter import Plotter

class LogPlotter(Plotter):
    def setup_plot(self, plot):
        # use logarithmic x-axis (e.g. for frequency sweeps)
        plot.setLogMode(x=True)

```

For [`ManagedWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindow), plot customization is broader because specialization is done with inheritance. [`ManagedWindowBase`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindowBase) provides the base class used by [`ManagedWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindow) and [`ManagedImageWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_image_window.ManagedImageWindow), while those subclasses are the GUI-ready window classes.
