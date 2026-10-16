# pymeasure.instruments.keysight.KeysightE3631A.values

[Owning PyMeasure class, adapter and connection contract](overview.md)

values(*command*, *separator='*, *'*, *cast=<class 'float'>*, *preprocess_reply=None*, *maxsplit=-1*, ***kwargs*)

Send a command to the instrument and return the result as a list of formatted values.

Parameters:

- **command** (`str`) – SCPI command sent to the instrument.

- **preprocess_reply** (`Optional`[`Callable`[[`str`], `str`]]) – Optional callable that handles the instrument response string before splitting; it returns the processed string. (default: `None`)

- **separator** (`Optional`[`str`]) – Character used to split the device response string into a list. None means split on any whitespace (see `str.split`). (default: `','`)

- **maxsplit** (`int`) – Maximum number of times to split the device response string. -1 (default) means unlimited splitting. (default: `-1`)

- **cast** (`Union`[`type`[`TypeVar`(`T`)], `Callable`[[`str`], `TypeVar`(`T`)]]) –

Type used to cast every element from the split string.

Deprecated since version 0.17.0: If a cast fails, the element remains a string. A future version will raise an error instead. To allow mixed types deliberately, use a dedicated function such as `cast_or_str()` as cast function. (default: `<class 'float'>`)

- ****kwargs** – Keyword arguments forwarded to the `ask()` method.

Returns:

`list`[`TypeVar`(`T`)] – A list containing the desired type; deprecated behavior allows str elements where casting fails.
