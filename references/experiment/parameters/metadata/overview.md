# pymeasure.experiment.parameters.Metadata

*class *pymeasure.experiment.parameters.Metadata(*name*, *fget=None*, *units=None*, *default=None*, *fmt='%s'*)

Represents experiment metadata, including the name plus the fget function and units when provided. Without an fget function, the value property returns the most recently assigned parameter value, or the default if no value has ever been set.

Variables:

**value** - The parameter value. If a value exists, this is the evaluated result from fget or a value assigned manually. Returns None when no value has been set

Parameters:

- **name** – The parameter name

- **fget** - The parameter fget function; pass either a callable or a string. When a string is used, it is interpreted as the method or attribute name on the Procedure class that defines the Metadata. A string can also refer to nested attributes by using a period separator, for example to reach an instrument attribute or method; in that nested path, only the final attribute may be a method. (default: `None`)

- **units** - Parameter units (default: `None`)

- **default** - Default value used when no value is assigned or no fget method is provided (default: `None`)

- **fmt** - String applied to format the value before writing it to a file. Default is "%s" (default: `'%s'`)
