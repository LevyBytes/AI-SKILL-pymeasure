# ManagedDockWindow axes, floating docks, layout persistence and tabs

[ManagedDockWindow setup changes and complete example](managed-dock-window-example.md)

We can now display the `ManagedDockWindow`:

 (Figure: Managed dock window)

The screenshot above shows that the example created three docks with these “X Axis” and “Y Axis” labels:

1. **X Axis:** “Iteration” **Y Axis:** “Random Number 1”

2. **X Axis:** “Random Number 1” **Y Axis:** “Random Number 2”

3. **X Axis:** “Random Number 1” **Y Axis:** “Random Number 3”

The string lists supplied to `x_axis` and `y_axis` provide the initial labels for each dockable plot. The number of dockable plots comes from whichever list is longest. In the example, `x_axis` and `y_axis` are defined like this:

```python
x_axis=['Iteration', 'Random Number 1'],
y_axis=['Random Number 1','Random Number 2', 'Random Number 3']

```

When one list is longer, the remaining dockable plots reuse the final element of the other list as their default label. That is why this example shows two **X Axis** labels set to “Random Number 1”. Between `x_axis` and `y_axis`, the longer list controls how many plots are built; here `y_axis` is longest, with a length of three, so three plots are created.

To detach a dockable plot into a separate window, double-click the blue “Dock #” title bar, which appears on the left side of each plot by default:

 (Figure: Managed dock window pop-up)

Close the popped-out window with the X icon in the top-right corner to return it to the main window.

Once the docks are arranged, save the layout by right-clicking a dock widget and choosing “Save Dock Layout” from the context menu. This writes one file containing every dock layout plus each plot setting. The default location is the current working directory of the python file that launched `ManagedDockWindow`. The default file name is ‘*procedure class* + “_dock_layout.json”’; in this example it becomes “./RandomProcedure_dock_layout.json”.

On the next run of the python file that calls `ManagedDockWindow`, the layout file is detected and loaded when it is present.

 (Figure: Save dock window layout)

Dockable plots can be rearranged relative to one another by dragging within the main dock window. Drag the blue “Dock #” title bar to the left or right edge of another plot to place the two plots side by side:

 (Figure: Side drag managed dock window) (Figure: Side position managed dock window)

Dragging the blue “Dock #” title bar to the top or bottom edge of another plot changes the vertical ordering of the plots:

 (Figure: Top position managed dock window)

Dragging the blue “Dock #” title bar onto the middle of another plot groups the two plots into a tabbed view:

 (Figure: Tab drag managed dock window) (Figure: Tab position managed dock window)
