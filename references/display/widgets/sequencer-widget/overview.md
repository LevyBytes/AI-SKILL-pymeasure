# pymeasure.display.widgets.sequencer_widget.SequencerWidget

*class *pymeasure.display.widgets.sequencer_widget.SequencerWidget(*inputs=None*, *sequence_file=None*, *parent=None*)

Bases: `QWidget`

Widget for creating a measurement sequence.

It supports parameter sweeps, can read a simple text file for loading a sequence, and can save sequences too.

Currently requires a queue function on [`ManagedWindow`](https://pymeasure.readthedocs.io/en/latest/api/display/windows.html#pymeasure.display.windows.managed_window.ManagedWindow) with a “procedure” argument.

Parameters:

**inputs** – List of strings naming the parameters (default: `None`)
