# pymeasure.experiment.parameters.Measurable

*class *pymeasure.experiment.parameters.Measurable(*name*, *fget=None*, *units=None*, *measure=True*, *default=None*, ***kwargs*)

Represents a measurable experiment parameter, including the name plus the fget function and units when provided. When the procedure retrieves a datapoint, the value property invokes the fget function. Without an fget function, the value property returns the most recently assigned parameter value, or the default if no value has ever been set.

Variables:

**value** - Current value of the parameter

Parameters:

- **name** – The parameter name

- **fget** - Parameter fget function, such as an instrument parameter (default: `None`)

- **default** - Default value (default: `None`)
