# pymeasure.display.widgets.console_widget.ConsoleWidget

*class *pymeasure.display.widgets.console_widget.ConsoleWidget(*name*, **args*, ***kwargs*)

Bases: `TabWidget`, `ConsoleWidget`

Show an interactive Python console inside the GUI.

Permit arbitrary Python commands to run at runtime and help debug the application.

It can be added to subclasses of [`ManagedWindowBase`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindowBase) by including it in the widget_list.

Parameters:

- **name** – Name for the widget, shown on the GUI tab.

- **parent** – The Qt parent widget.

- **namespace** – A dictionary containing variables and modules exposed to the console. For example, `{'window': self, 'device': your_device}`.

- **text** – The welcome message initially shown in the console.
