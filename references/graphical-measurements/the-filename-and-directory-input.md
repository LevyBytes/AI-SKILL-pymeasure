# The filename and directory input

A ManagedWindow instance includes filename and directory fields by default. These fields are part of [`FileInputWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.fileinput_widget.FileInputWidget) and determine where experiment results are saved.

 [(Figure: Filename and directory controls)](https://pymeasure.readthedocs.io/en/latest/_images/pymeasure-fileinput.png) [(Figure: Filename and directory controls with saving disabled for temporary-file storage)](https://pymeasure.readthedocs.io/en/latest/_images/pymeasure-fileinput_disabled.png) [(Figure: Filename field auto-complete)](https://pymeasure.readthedocs.io/en/latest/_images/pymeasure-fileinput_complete_filename.png) [(Figure: Directory field auto-complete)](https://pymeasure.readthedocs.io/en/latest/_images/pymeasure-fileinput_complete_directory.png)

When Save data is checked, the measurement is saved to a file. When it is unchecked, data is written to a temporary file instead.

The filename field accepts values with or without an extension. If the supplied extension is recognized, `.csv` and `.txt` by default, it is kept. For an unrecognized extension, the first available extension is chosen; by default that is `.csv`. A sequence number is also inserted immediately before the extension so each filename remains unique.

Filenames may include placeholders resolved by python's standard `format` function. Enter placeholders in the form `'{placeholder name:formatspec}'`. Accepted placeholder names come from every input parameter and from the measurement procedure metadata; the field tooltip lists the valid names. Since standard `format` handling is used, format specs work normally. For instance, `'DATA_delay{Delay Time:08.3f}s'` is rendered as `'DATA_delay0000.010s'`.

Auto-completion is available in both the filename field and the directory field. The directory field also has a right-side button that opens a folder-selection window.

After [`ManagedWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindow) initialization, you can set these defaults directly. That covers the default directory, default filename, recognized extensions, the initial Save data toggle value, and whether users may edit the filename field.

```python
from pymeasure.display.windows.managed_window import ManagedWindow

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

        self.filename = r'default_filename_delay{Delay Time:4f}s'   # Sets default filename
        self.directory = r'C:/Path/to/default/directory'            # Sets default directory
        self.store_measurement = False                              # Controls the 'Save data' toggle
        self.file_input.extensions = ["csv", "txt", "data"]         # Sets recognized extensions, first entry is the default extension
        self.file_input.filename_fixed = False                      # Controls whether the filename-field is frozen (but still displayed)

```

The boolean `enabled_file_input` argument on [`ManagedWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindow) init determines whether this widget appears. If enabled_file_input is `False`, the default [`queue()`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindowBase.queue) implementation supplied by [`ManagedWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindow) no longer functions. You must provide a custom replacement; the [`queue()`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindowBase.queue) method documentation includes a simple version.
