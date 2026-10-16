# Instrument file

Every standard instrument should subclass [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument). That base supplies the core behavior for using [`Adapters`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.Adapter), which handle the real communication.

For the "Extreme 5000" example, the simplest instrument begins this way:

```python

# This file is part of the PyMeasure package.

# Copyright (c) 2013-2026 PyMeasure Developers

# Permission is hereby granted, free of charge, to any person obtaining a copy
# of this software and associated documentation files (the "Software"), to deal
# in the Software without restriction, including without limitation the rights
# to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
# copies of the Software, and to permit persons to whom the Software is
# furnished to do so, subject to the following conditions:

# The above copyright notice and this permission notice shall be included in
# all copies or substantial portions of the Software.

# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
# AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
# OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
# THE SOFTWARE.

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
