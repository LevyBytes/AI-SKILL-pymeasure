# Using tabular format

Some experiments benefit from tabular data alongside a graph, or instead of one. [`ManagedWindowBase`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindowBase) can include a [`TableWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.table_widget.TableWidget) for displaying experiment data; the widget can also export to common formats such as CSV, HTML, etc. The example below customizes [`ManagedWindowBase`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindowBase) for tabular output, derives from the earlier example, and marks the changed lines.

The complete program is in the [upstream source](https://raw.githubusercontent.com/pymeasure/pymeasure/08c4a91f5255c937a909cc21e70fa3fafd76333e/docs/tutorial/graphical.rst).

The resulting GUI display appears below.

 (Figure: TableWidget Example)
