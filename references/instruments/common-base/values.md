# pymeasure.instruments.common_base.CommonBase.values

[Owning PyMeasure class, adapter and connection contract](overview.md)

values(*command*, *separator='*, *'*, *cast=<class 'float'>*, *preprocess_reply=None*, *maxsplit=-1*, ***kwargs*)

Send a command to the instrument and return formatted values parsed from the reply.

Parameters:

- **command** (`str`) - SCPI command sent to the instrument.

- **preprocess_reply** (`Optional`[`Callable`[[`str`], `str`]]) - Optional callable that transforms the instrument reply string before it is split. It returns the transformed string. (default: `None`)

- **separator** (`Optional`[`str`]) - Separator character used to divide the returned device string into a list. None uses whitespace splitting; see `str.split`. (default: `','`)

- **maxsplit** (`int`) - Maximum number of splits applied to the device return string. -1, the default, means unlimited splitting. (default: `-1`)

- **cast** (`Union`[`type`[`TypeVar`(`T`)], `Callable`[[`str`], `TypeVar`(`T`)]]) –

Type used to cast every item from the split string.

Deprecated since version 0.17.0: When casting is unsuccessful, that element remains a string. A later release will raise an error for that situation. To intentionally permit mixed types, provide a dedicated function, such as `cast_or_str()` as cast function. (default: `<class 'float'>`)

- ****kwargs** - Keyword arguments passed through to the `ask()` method.

Returns:

`list`[`TypeVar`(`T`)] - List containing the requested type, or, in deprecated behavior, str entries where casting fails.
