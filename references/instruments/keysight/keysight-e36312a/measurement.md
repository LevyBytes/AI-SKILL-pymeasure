# pymeasure.instruments.keysight.KeysightE36312A.measurement

[Owning PyMeasure class, adapter and connection contract](overview.md)

*static *measurement(*get_command*, *docs*, *values=()*, *map_values=False*, *get_process=<function CommonBase.&lt;lambda&gt;>*, *get_process_list=<function CommonBase.&lt;lambda&gt;>*, *check_get_errors=False*, *dynamic=False*, *preprocess_reply=None*, *separator='*, *'*, *maxsplit=-1*, *cast=<class 'float'>*, *values_kwargs=None*)

Create a class property from the supplied commands. This measurement quantity is read-only for the instrument and cannot be set.

Parameters:

- **get_command** (`str`) — String command that requests the value

- **docs** (`str`) — Docstring text included in the documentation

- **values** (`Any`) — List, tuple, range, or dictionary of valid values; when `map_values` is True, it may also map values. (default: `()`)

- **map_values** (`bool`) — Boolean flag selecting whether values are treated as a map. (default: `False`)

- **get_process** (`Callable`[[`Any`], `Any`]) — Function that receives a value for processing before value mapping and returns the processed value. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f8510>`)

- **get_process_list** (`Callable`[[`list`[`Any`]], `Any`]) — Function that receives the value list and processes it. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f85c0>`)

- **check_get_errors** (`bool`) — Enables or disables error checking after getting. (default: `False`)

- **dynamic** (`bool`) — Indicates whether property parameters are intended to be changed on instances or subclasses. See `control()` for a usage example. (default: `False`)

- **preprocess_reply** (`Optional`[`Callable`[[`str`], `str`]]) — Optional callable that processes the instrument response string before splitting; it returns the processed string. (default: `None`)

- **separator** (`Optional`[`str`]) — Character used to split the device response string into a list. None splits on any whitespace (see `str.split`). (default: `','`)

- **maxsplit** (`int`) — Maximum number of split operations applied to the device response string. -1 (default) means unlimited splitting. (default: `-1`)

- **cast** (`Callable`[[`str`], `TypeVar`(`T`)]) –

Type used to cast every element from the split string.

Deprecated since version 0.17.0: When casting fails, that element remains a string; see `values()`. To permit mixed types deliberately, pass `cast_or_str()` as the cast function. (default: `<class 'float'>`)

- **values_kwargs** (*dict*) — Additional keyword arguments for `values()`.

Return type:

`Union`[`property`, `DynamicProperty`]
