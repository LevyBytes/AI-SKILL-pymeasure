# Install with pip

`pip` is another supported way to install PyMeasure.

```bash
pip install pymeasure

```

To enable live-plotting and GUI support, install the `gui` extra together with a Qt binding:

```bash
pip install pymeasure[gui] PyQt5

```

Depending on your preference, `PyQt5` may be substituted with `PyQt6`, `PySide2`, or `PySide6`. A `conda` installation brings in Qt libraries automatically; a `pip` installation requires you to add one explicitly.
