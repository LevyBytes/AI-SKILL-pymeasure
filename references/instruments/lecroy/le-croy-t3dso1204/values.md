# pymeasure.instruments.lecroy.LeCroyT3DSO1204.values

[Owning PyMeasure class, adapter and connection contract](overview.md)

values(*command*, *separator='*, *'*, *cast=<class 'float'>*, *preprocess_reply=None*, *maxsplit=-1*, ***kwargs*)

Send a command to the instrument and return the reply as a list of formatted values.

Parameters:

- **command** (`str`) - SCPI command sent to the instrument.

- **preprocess_reply** (`Optional`[`Callable`[[`str`], `str`]]) - Optional callable run on the instrument reply string before splitting; it returns that processed string. (default: `None`)

- **separator** (`Optional`[`str`]) - Separator character used to split the device-returned string into a list. None means split on any whitespace; see `str.split`. (default: `','`)

- **maxsplit** (`int`) - Maximum number of splits to apply to the string returned by the device. `-1` (default) means unlimited. (default: `-1`)

- **cast** (`Union`[`type`[`TypeVar`(`T`)], `Callable`[[`str`], `TypeVar`(`T`)]]) –

Type used to cast every element from the split string.

Deprecated since version 0.17.0: if casting fails, that element remains a string. A future version will raise an error instead. To allow mixed types explicitly, pass a dedicated function, for example `cast_or_str()` as the cast function. (default: `<class 'float'>`)

- ****kwargs** - Keyword arguments forwarded to the `ask()` method.

Returns:

`list`[`TypeVar`(`T`)] - List containing the requested type, or, in deprecated behavior, str for elements where casting fails.
