# pymeasure.experiment.parameters.ListParameter

*class *pymeasure.experiment.parameters.ListParameter(*name*, *choices=None*, *units=None*, ***kwargs*)

`Parameter` subclass that keeps the value as a list. The string representation of each choice must be unique.

Parameters:

- **name** – The parameter name

- **choices** - Explicit list of choices; it is disregarded if None (default: `None`)

- **units** - Units of measure for the parameter (default: `None`)

- **default** – The default value

- **ui_class** - Qt class used for this parameter's UI

## Related property contracts

- Open when checking pymeasure.experiment.parameters.ListParameter.choices: [choices](choices.md).
