# Defining your own ManagedWindow’s widgets

In the [`ManagedWindowBase`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindowBase) constructor, the `widget_list` parameter lets you add user-defined widgets to the GUI results display area. A user widget should inherit from [`TabWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.tab_widget.TabWidget) and may reimplement whichever methods require custom behavior. To understand the mechanism, review these built-in widgets:

- [`LogWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.log_widget.LogWidget)

- [`PlotWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.plot_widget.PlotWidget)

- [`ImageWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.image_widget.ImageWidget)

- `DockWidget`

- [`TableWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.table_widget.TableWidget)

- [`ConsoleWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.console_widget.ConsoleWidget)
