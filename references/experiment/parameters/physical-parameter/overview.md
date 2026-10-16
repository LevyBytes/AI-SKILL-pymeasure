# pymeasure.experiment.parameters.PhysicalParameter

*class *pymeasure.experiment.parameters.PhysicalParameter(*name*, *uncertaintyType='absolute'*, ***kwargs*)

`VectorParameter` subclass with 2 dimensions; it stores a value together with its uncertainty.

Variables:

**value** - Parameter value as a list of 2 floating point numbers

Parameters:

- **name** – The parameter name

- **uncertainty_type** - Uncertainty type: 'absolute', 'relative', or 'percentage'

- **units** - Units of measure for the parameter

- **default** – The default value

- **ui_class** - Qt class used for this parameter's UI
