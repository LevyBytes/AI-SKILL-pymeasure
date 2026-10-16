# pymeasure.instruments.keysight.KeysightE36312A.values

[Owning PyMeasure class, adapter and connection contract](overview.md)

values(*command*, *separator='*, *'*, *cast=<class 'float'>*, *preprocess_reply=None*, *maxsplit=-1*, ***kwargs*)

Send a command to the instrument and return the result as a list of formatted values.

Parameters:

- **command** (`str`) — SCPI command sent to the instrument.

- **preprocess_reply** (`Optional`[`Callable`[[`str`], `str`]]) — Optional callable that processes the instrument response string before splitting; it returns the processed string. (default: `None`)

- **separator** (`Optional`[`str`]) — Character used to split the device response string into a list. None splits on any whitespace (see `str.split`). (default: `','`)

- **maxsplit** (`int`) — Maximum number of split operations applied to the device response string. -1 (default) means unlimited splitting. (default: `-1`)

- **cast** (`Union`[`type`[`TypeVar`(`T`)], `Callable`[[`str`], `TypeVar`(`T`)]]) –

Type used to cast every element from the split string.

Deprecated since version 0.17.0: When casting fails, that element remains a string. A later version will raise an error instead. To permit mixed types deliberately, use a dedicated function, for example `cast_or_str()` as cast function. (default: `<class 'float'>`)

- ****kwargs** — Keyword arguments forwarded to the `ask()` method.

Returns:

`list`[`TypeVar`(`T`)] — List of the desired type, or, where casting fails, the deprecated str fallback.
