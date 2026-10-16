# Using the sequencer

[Prior ManagedWindow and Procedure setup](managed-window-example.md)

Beyond graphical parameter entry and multi-measurement execution through [`ManagedWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindow), [`SequencerWidget`](https://pymeasure.readthedocs.io/en/latest/api/display/widgets.html#pymeasure.display.widgets.sequencer_widget.SequencerWidget) lets users enqueue a series of measurements while varying one, or more, parameters. The sequencer is therefore a convenient tool for scanning the measurement procedure's parameter space.
Enable the sequencer by supplying two extra keyword arguments to [`ManagedWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindow): `sequencer` and `sequencer_inputs`. Set `sequencer` to a boolean that controls whether the window includes the sequencer. For `sequencer_inputs`, pass `None` or a list containing the parameter names to scan. When that list is omitted, the manager queue display determines the parameters.

To make the sequencer usable, [`ManagedWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindow) must provide a `queue` method. That method should accept a keyword argument, preferably keyword-only for safety, named `procedure`; pass the procedure instance through that argument. The sequencer calls this method when it queues the parameter scan.

To add the sequencer to the earlier example, only [`ManagedWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindow) needs a small adjustment; the changed lines are marked below:

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
            sequencer=True,                                      # Added line
            sequencer_inputs=['iterations', 'delay', 'seed'],    # Added line
            sequence_file="gui_sequencer_example_sequence.txt",  # Added line, optional
        )
        self.setWindowTitle('GUI Example')

```

This places the sequencer below the input panel.

 (Figure: Sequencer widget example)

The widget includes a tree-view for composing the sequence. It presents three columns: `level` (showing the nesting depth for an item), `parameter` (a drop-down menu for choosing the parameter that item sequences), and `sequence` (the text-box used to enter the sequence). The first two columns are mostly self-explanatory; the final one needs more detail.

For flexible sequence entry, the sequence is written in a text-box where the user may type any single-line expression that produces a list. Several helpers are available for that expression: from the main python library, `range`, `sorted`, and `list`; from numpy, the functions listed below. You do not need to prefix them with `numpy.` or any abbreviation. Available numpy names are `arange`, `linspace`, `arccos`, `arcsin`, `arctan`, `arctan2`, `ceil`, `cos`, `cosh`, and `degrees`; the list continues with `e`, `exp`, `fabs`, `floor`, `fmod`, `frexp`, `hypot`, `ldexp`, and `log`; it also includes `log10`, `modf`, `pi`, `power`, `radians`, `sin`, `sinh`, `sqrt`, `tan`, and `tanh`.

For example, `arange(0, 10, 1)` returns values separated by 1, while `exp(arange(0, 10, 1))` turns those values into an exponentially growing sequence. This makes more elaborate sequences practical to enter.

Use `Add root item`, `Add item`, and `Remove item` to grow or trim the sequence. The add-child control creates a child under the currently selected entry, while the remove control deletes the selected entry. Press the `Queue` sequence button to enqueue the sequence that was entered. If any sequence text-box cannot be evaluated, the logger reports the error and nothing is queued.

You can also create a sequence file so the user does not have to retype the same sequence each time. Save the sequence currently built in the GUI with `Save sequence`, or write a simple text file directly. After the file exists, load it with `Load sequence`.

Each line in the sequence file contributes one item to the sequence tree. The line begins with dashes (`-`) to encode the item level, with 1 dash meaning top level, then gives the parameter name and sequence string, both written as a python string between parentheses.

Below is an example sequence file that produces the sequence displayed in the preceding figure.

```text
- "Delay Time", "arange(0.25, 1, 0.25)"
-- "Random Seed", "[1, 4, 8]"
--- "Loop Iterations", "exp(linspace(1, 5, 3))"
-- "Random Seed", "arange(10, 100, 10)"

```

This file can be loaded automatically when the program starts by adding `sequence_file="filename.txt"` as a key-word argument in the `super().__init__` call, matching the example.
