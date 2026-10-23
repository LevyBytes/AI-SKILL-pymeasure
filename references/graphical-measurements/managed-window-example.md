# ManagedWindow complete Procedure and MainWindow example

[ManagedWindow queue, abort/resume and plot-linewidth behavior](managed-window-queue-control.md)

ManagedWindow is the easiest way to launch measurements built from your Procedure. Its main benefit is graphical entry for input parameters: the parameters automatically become form fields where users can type values. This lets a measurement be configured at run time instead of being hard-coded in a script.

ManagedWindow also supports a sequential queue for measurements. You can prepare multiple runs with different input parameters and observe them on the live-plot as they execute, which is valuable for long running measurements. Internally, the Manager tells the Worker which Procedure to execute and monitors the Worker status while it advances.

The next example revises the earlier code so it uses a ManagedWindow.

The complete program is in the [upstream source](https://raw.githubusercontent.com/pymeasure/pymeasure/08c4a91f5255c937a909cc21e70fa3fafd76333e/docs/tutorial/graphical.rst).
