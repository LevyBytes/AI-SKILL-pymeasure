# pymeasure.instruments.keysight.Keysight81160A.values

[Owning PyMeasure class, adapter and connection contract](overview.md)

values(*command*, *separator='*, *'*, *cast=<class 'float'>*, *preprocess_reply=None*, *maxsplit=-1*, ***kwargs*)

Send a command to the instrument and return the response as a list of formatted values.

Parameters:

- **command** (`str`) – SCPI command sent to the instrument.

-
**preprocess_reply** (`Optional`[`Callable`[[`str`], `str`]]) - Optional callable that transforms the instrument reply string before it is split, returning that processed string. (default: `None`)

- **separator** (`Optional`[`str`]) - Character used as the delimiter that turns the device reply string into a list. None splits on any whitespace; see `str.split`. (default: `','`)

- **maxsplit** (`int`) - The returned device string is split no more than maxsplit times. -1 (default) means unlimited splitting. (default: `-1`)

- **cast** (`Union`[`type`[`TypeVar`(`T`)], `Callable`[[`str`], `TypeVar`(`T`)]]) –

Type used to cast every item produced by splitting the string.

Deprecated since version 0.17.0: When a cast operation fails, that element remains a string. A later version will raise an error instead. To permit mixed types deliberately, supply a dedicated function, for example `cast_or_str()` as cast function. (default: `<class 'float'>`)

- ****kwargs** - Keyword arguments forwarded to the `ask()` method.

Returns:

`list`[`TypeVar`(`T`)] - List containing the requested type, or, while deprecated behavior remains, str entries where casting fails.
