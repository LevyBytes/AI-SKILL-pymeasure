# ManagedConsole selection and complete console/GUI example

[ManagedConsole invocation and optional progress display](console-invocation.md)

For command-line measurements with a Procedure, [`ManagedConsole`](https://pymeasure.readthedocs.io/en/latest/api/display/console.html#pymeasure.display.console.ManagedConsole) is the simplest interface. The same [`ManagedConsole`](https://pymeasure.readthedocs.io/en/latest/api/display/console.html#pymeasure.display.console.ManagedConsole) runs an experiment using the same parameters exposed by [`ManagedWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindow), but those parameters are supplied through command line switches.

It is possible to write a test that chooses either [`ManagedConsole`](https://pymeasure.readthedocs.io/en/latest/api/display/console.html#pymeasure.display.console.ManagedConsole) or [`ManagedWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindow) based on the user command line selection.

Console mode can be enabled with little setup; the example below shows the pattern.

The next example adapts the Using the ManagedWindow code and highlights the relevant sections:

1. Line 8 now imports [`ManagedConsole`](https://pymeasure.readthedocs.io/en/latest/api/display/console.html#pymeasure.display.console.ManagedConsole).

2. Line 73, adds console mode support.

The complete program is in the [upstream source](https://raw.githubusercontent.com/pymeasure/pymeasure/08c4a91f5255c937a909cc21e70fa3fafd76333e/examples/Basic/console.py).
