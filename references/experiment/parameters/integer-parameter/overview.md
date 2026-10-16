# pymeasure.experiment.parameters.IntegerParameter

*class *pymeasure.experiment.parameters.IntegerParameter(*name*, *units=None*, *minimum=-1000000000.0*, *maximum=1000000000.0*, *step=None*, ***kwargs*)

`Parameter` subclass that stores its value using the integer type.

Variables:

**value** - Integer value held by the parameter

Parameters:

- **name** – The parameter name

- **units** - Units of measure for the parameter (default: `None`)

- **minimum** - Lowest allowed value (default: -1e9) (default: `-1000000000.0`)

- **maximum** - Highest allowed value (default: 1e9) (default: `1000000000.0`)

- **default** – The default integer value

- **ui_class** - Qt class used for this parameter's UI

- **step** - int step size for the parameter's UI spinbox. When None, the spinbox step is disabled (default: `None`)
