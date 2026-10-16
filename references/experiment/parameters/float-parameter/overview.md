# pymeasure.experiment.parameters.FloatParameter

*class *pymeasure.experiment.parameters.FloatParameter(*name*, *units=None*, *minimum=-1000000000.0*, *maximum=1000000000.0*, *decimals=15*, *step=None*, ***kwargs*)

`Parameter` subclass that stores its value using the floating point type.

Variables:

**value** - Floating point value held by the parameter

Parameters:

- **name** – The parameter name

- **units** - Units of measure for the parameter (default: `None`)

- **minimum** - Lowest allowed value (default: -1e9) (default: `-1000000000.0`)

- **maximum** - Highest allowed value (default: 1e9) (default: `1000000000.0`)

- **decimals** - Number of decimals taken into account (default: 15) (default: `15`)

- **default** - Default floating point value

- **ui_class** - Qt class used for this parameter's UI

- **step** - Step size for the parameter's UI spinbox. When None, the spinbox step is disabled (default: `None`)
