# Parameters

> Pymeasure reference. Original prose; identifiers preserved verbatim.

### Parameter classes

Parameter classes define input variables for a [`Procedure`](https://pymeasure.readthedocs.io/en/latest/api/experiment/procedure.html#pymeasure.experiment.procedure.Procedure). Every one derives from the `Parameter` base class.

 Class constructor: *pymeasure.experiment.parameters.BooleanParameter* accepts *name*, *default=None*, *ui_class=None*, *group_by=None*, *group_condition=True*, and *description=None*.

`Parameter` subclass that stores its value using the boolean type.

Variables:

**value** - Boolean value held by the parameter

Parameters:

-

**name** – The parameter name

-

**default** - Default boolean value (default: `None`)

-

**ui_class** - Qt class used for this parameter's UI (default: `None`)

 convert(*value*)

Transform user input into python data format

Subclasses should override this method as needed. The default behavior is the identity function

Parameters:

**value** – value to be converted

Returns:

converted value

 *class *pymeasure.experiment.parameters.FloatParameter(*name*, *units=None*, *minimum=-1000000000.0*, *maximum=1000000000.0*, *decimals=15*, *step=None*, ***kwargs*)

`Parameter` subclass that stores its value using the floating point type.

Variables:

**value** - Floating point value held by the parameter

Parameters:

-

**name** – The parameter name

-

**units** - Units of measure for the parameter (default: `None`)

-

**minimum** - Lowest allowed value (default: -1e9) (default: `-1000000000.0`)

-

**maximum** - Highest allowed value (default: 1e9) (default: `1000000000.0`)

-

**decimals** - Number of decimals taken into account (default: 15) (default: `15`)

-

**default** - Default floating point value

-

**ui_class** - Qt class used for this parameter's UI

-

**step** - Step size for the parameter's UI spinbox. When None, the spinbox step is disabled (default: `None`)

 convert(*value*)

Transform user input into python data format

Subclasses should override this method as needed. The default behavior is the identity function

Parameters:

**value** – value to be converted

Returns:

converted value

 *class *pymeasure.experiment.parameters.IntegerParameter(*name*, *units=None*, *minimum=-1000000000.0*, *maximum=1000000000.0*, *step=None*, ***kwargs*)

`Parameter` subclass that stores its value using the integer type.

Variables:

**value** - Integer value held by the parameter

Parameters:

-

**name** – The parameter name

-

**units** - Units of measure for the parameter (default: `None`)

-

**minimum** - Lowest allowed value (default: -1e9) (default: `-1000000000.0`)

-

**maximum** - Highest allowed value (default: 1e9) (default: `1000000000.0`)

-

**default** – The default integer value

-

**ui_class** - Qt class used for this parameter's UI

-

**step** - int step size for the parameter's UI spinbox. When None, the spinbox step is disabled (default: `None`)

 convert(*value*)

Transform user input into python data format

Subclasses should override this method as needed. The default behavior is the identity function

Parameters:

**value** – value to be converted

Returns:

converted value

 *class *pymeasure.experiment.parameters.ListParameter(*name*, *choices=None*, *units=None*, ***kwargs*)

`Parameter` subclass that keeps the value as a list. The string representation of each choice must be unique.

Parameters:

-

**name** – The parameter name

-

**choices** - Explicit list of choices; it is disregarded if None (default: `None`)

-

**units** - Units of measure for the parameter (default: `None`)

-

**default** – The default value

-

**ui_class** - Qt class used for this parameter's UI

 *property *choices

Returns an immutable iterable of choices, or None when choices are unset.

 convert(*value*)

Transform user input into python data format

Subclasses should override this method as needed. The default behavior is the identity function

Parameters:

**value** – value to be converted

Returns:

converted value

 *class *pymeasure.experiment.parameters.Measurable(*name*, *fget=None*, *units=None*, *measure=True*, *default=None*, ***kwargs*)

Represents a measurable experiment parameter, including the name plus the fget function and units when provided. When the procedure retrieves a datapoint, the value property invokes the fget function. Without an fget function, the value property returns the most recently assigned parameter value, or the default if no value has ever been set.

Variables:

**value** - Current value of the parameter

Parameters:

-

**name** – The parameter name

-

**fget** - Parameter fget function, such as an instrument parameter (default: `None`)

-

**default** - Default value (default: `None`)

 *class *pymeasure.experiment.parameters.Metadata(*name*, *fget=None*, *units=None*, *default=None*, *fmt='%s'*)

Represents experiment metadata, including the name plus the fget function and units when provided. Without an fget function, the value property returns the most recently assigned parameter value, or the default if no value has ever been set.

Variables:

**value** - The parameter value. If a value exists, this is the evaluated result from fget or a value assigned manually. Returns None when no value has been set

Parameters:

-

**name** – The parameter name

-

**fget** - The parameter fget function; pass either a callable or a string. When a string is used, it is interpreted as the method or attribute name on the Procedure class that defines the Metadata. A string can also refer to nested attributes by using a period separator, for example to reach an instrument attribute or method; in that nested path, only the final attribute may be a method. (default: `None`)

-

**units** - Parameter units (default: `None`)

-

**default** - Default value used when no value is assigned or no fget method is provided (default: `None`)

-

**fmt** - String applied to format the value before writing it to a file. Default is "%s" (default: `'%s'`)

 is_set()

Returns True when the Parameter value has been set

 Class constructor: *pymeasure.experiment.parameters.Parameter* accepts *name*, *default=None*, *ui_class=None*, *group_by=None*, *group_condition=True*, and *description=None*.

Represents an experiment parameter, including the name and units when provided.

Variables:

**value** - Current value of the parameter

Parameters:

-

**name** – The parameter name

-

**default** - Default value (default: `None`)

-

**ui_class** - Qt class used for this parameter's UI (default: `None`)

-

**group_by** - Identifies the Parameter(s) controlling whether the associated input is visible. It may be one string for a Parameter name, a dict containing {"Parameter name": condition} pairs, or a list of strings when multiple Parameter names are involved. (default: `None`)

-

**group_condition** - Condition checked against the group_by Parameter to control this parameter's visibility; provide it as a value or a (lambda)function. When the group_by argument is a list of strings, this argument may be either one condition or a list of conditions. When the group_by argument is a dict, this argument is ignored. (default: `True`)

Description:

A human-friendly description string for the parameter.

 *property *cli_args

helper for parsing parameters in a command line interface

This property supplies data for formatting a command line interface interpreter, returned as a list with these elements: - index 0: default value - index 1: values for formatting an help string, either the documented field names or a tuple with (helps_string, field) - index 2: type

 convert(*value*)

Transform user input into python data format

Subclasses should override this method as needed. The default behavior is the identity function

Parameters:

**value** – value to be converted

Returns:

converted value

 is_set()

Returns True when the Parameter value has been set

 *class *pymeasure.experiment.parameters.PhysicalParameter(*name*, *uncertaintyType='absolute'*, ***kwargs*)

`VectorParameter` subclass with 2 dimensions; it stores a value together with its uncertainty.

Variables:

**value** - Parameter value as a list of 2 floating point numbers

Parameters:

-

**name** – The parameter name

-

**uncertainty_type** - Uncertainty type: 'absolute', 'relative', or 'percentage'

-

**units** - Units of measure for the parameter

-

**default** – The default value

-

**ui_class** - Qt class used for this parameter's UI

 convert(*value*)

Transform user input into python data format

Subclasses should override this method as needed. The default behavior is the identity function

Parameters:

**value** – value to be converted

Returns:

converted value

 *class *pymeasure.experiment.parameters.VectorParameter(*name*, *length=3*, *units=None*, ***kwargs*)

`Parameter` subclass that stores the value in vector format.

Variables:

**value** - Parameter value as a list of floating point numbers

Parameters:

-

**name** – The parameter name

-

**length** - Integer dimensions of the vector (default: `3`)

-

**units** - Units of measure for the parameter (default: `None`)

-

**default** – The default value

-

**ui_class** - Qt class used for this parameter's UI

 convert(*value*)

Transform user input into python data format

Subclasses should override this method as needed. The default behavior is the identity function

Parameters:

**value** – value to be converted

Returns:

converted value
