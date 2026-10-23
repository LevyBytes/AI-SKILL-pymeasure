# Using the Plotter

Plotter does not include the richer conveniences of ManagedWindow, but it is the shortest path to live-plotting. Given a Results object, it refreshes the graph on a regular interval by reading the newest data from the file.

Warning

This section's example is known to cause runtime problems. One possible warning says that a QApplication was not created in the main thread, and another notes that nextEventMatchingMask should only be called from the Main Thread. Although some operating systems and python setups run it successfully, do not depend on the plotter until the issue is fixed. It is acceptable to skip ahead to Using the ManagedWindow section for a ManagedWindow-based workflow.

Expand SimpleProcedure into RandomProcedure, which emits random numbers during the loop. Instruments are omitted here so the example stays minimal.

The complete program is in the [upstream source](https://raw.githubusercontent.com/pymeasure/pymeasure/08c4a91f5255c937a909cc21e70fa3fafd76333e/docs/tutorial/graphical.rst).

The key change is that the Results object is used to create the Plotter.

```python
plotter = Plotter(results)
plotter.start()

```

The Plotter runs in a separate process, allowing it to use another CPU and improve performance. It opens a Qt graphical interface through pyqtgraph, where Results data can be displayed according to the columns present in the data.

 (Figure: Results Plotter Example)
