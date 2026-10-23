# ManagedDockWindow setup changes and complete example

[ManagedDockWindow axes, floating docks, layout persistence and tabs](dock-layout-and-axes.md)

Starting from the Using the ManagedWindow example that uses `ManagedWindow`, you can switch to [`ManagedDockWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_dock_window.ManagedDockWindow) to create a GUI with multiple graphs. Those graphs can stay docked in the main GUI window or be popped out into separate windows.

First, apply the highlighted edits below to the Using the ManagedWindow code example:

1. Line 10 now imports [`ManagedDockWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_dock_window.ManagedDockWindow).

2. Line 20, along with lines 32 and 33, adds two extra recorded data columns: `'Random Number 2'` and `'Random Number 3'`.

3. Line 44 changes `MainWindow` so it subclasses `ManagedDockWindow`.

4. Line 51 passes a list of strings taken from `DATA_COLUMNS` into the `x_axis` argument.

5. Line 52 passes a list of strings from `DATA_COLUMNS` into the `y_axis` argument.

The complete program is in the [upstream source](https://raw.githubusercontent.com/pymeasure/pymeasure/08c4a91f5255c937a909cc21e70fa3fafd76333e/docs/tutorial/graphical.rst).
