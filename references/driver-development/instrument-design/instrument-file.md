# Instrument file

Every standard instrument should subclass [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument). That base supplies the core behavior for using [`Adapters`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.Adapter), which handle the real communication.

A driver file contributed to PyMeasure opens with the project's license header, copied unchanged from any existing file in `pymeasure/instruments`. For the "Extreme 5000" example, the code then begins this way:

```python
from pymeasure.instruments import Instrument
```

A minimal instrument definition is:

```python
class Extreme5000(Instrument):
    """Control the imaginary Extreme 5000 instrument."""

    def __init__(self, adapter, name="Extreme 5000", **kwargs):
        super().__init__(
            adapter,
            name,
            **kwargs
        )

```

Add the PyMeasure license to every file, and list yourself as an author in `AUTHORS.txt`.

Instrument classes are easier to read when their elements follow this order:

- Place the initializer, the `__init__()` method, first so it is quick to locate while reading the source code.

- After that, add class attributes/variables when you need them.

- Next come properties, either pymeasure-specific or ordinary Python versions; this section usually contains most of the implementation.

- Finally, any methods.
