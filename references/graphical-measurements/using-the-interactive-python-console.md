# Using the interactive Python console

During a running application, it can be useful to inspect state or control an instrument interactively. PyMeasure supplies a [`ConsoleWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.console_widget.ConsoleWidget) that can be embedded directly inside [`ManagedWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindow).

Expose variables, instruments, and modules to the console by passing a `namespace` dictionary at initialization. Since [`ManagedWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindow) appends its default widgets, such as the plot and log, to the end of `widget_list`, a common pattern is to append [`ConsoleWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.console_widget.ConsoleWidget) manually after `super().__init__()` when you want it as the right-most tab.

```python
from pymeasure.display.windows.managed_window import ManagedWindow

from pymeasure.display.widgets.console_widget import ConsoleWidget

class MainWindow(ManagedWindow):

    def __init__(self):
        super().__init__(
            procedure_class=RandomProcedure,
            inputs=['iterations', 'delay', 'seed'],
            displays=['iterations', 'delay', 'seed'],
            x_axis='Iteration',
            y_axis='Random Number',
        )
        self.setWindowTitle('GUI Example')

        # 1. Create the console widget and expose variables to it
        self.console_widget = ConsoleWidget(
            "Script Console",
            namespace={
                'window': self,
                'device': '<your_instrument>', # replace with your instrument instance
                'np': '<numpy_module>' # replace with numpy if imported
            }
        )

        # 2. Append it manually so it appears as the last tab
        self.widget_list += (self.console_widget,)
        self.tabs.addTab(self.console_widget, self.console_widget.name)

```
