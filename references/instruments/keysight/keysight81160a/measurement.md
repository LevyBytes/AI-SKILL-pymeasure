# pymeasure.instruments.keysight.Keysight81160A.measurement

[Owning PyMeasure class, adapter and connection contract](overview.md)

*static *measurement(*get_command*, *docs*, *values=()*, *map_values=False*, *get_process=<function CommonBase.&lt;lambda&gt;>*, *get_process_list=<function CommonBase.&lt;lambda&gt;>*, *check_get_errors=False*, *dynamic=False*, *preprocess_reply=None*, *separator='*, *'*, *maxsplit=-1*, *cast=<class 'float'>*, *values_kwargs=None*)

Create a class property from the supplied commands. This measurement quantity is read-only from the instrument and cannot be set.

Parameters:

- **get_command** (`str`) – String command that requests the value

- **docs** (`str`) – Docstring text inserted into the documentation

- **values** (`Any`) – Valid values supplied as a list, tuple, range, or dictionary; when `map_values` is True this may also map values. (default: `()`)

- **map_values** (`bool`) – Boolean flag selecting whether values are treated as a map (default: `False`)

- **get_process** (`Callable`[[`Any`], `Any`]) – Function that receives a value, can transform it before value mapping, and returns the transformed value (default: `<function CommonBase.<lambda> at 0x7aa5aa7f8510>`)

- **get_process_list** (`Callable`[[`list`[`Any`]], `Any`]) – Function that receives the value list and returns its processed form. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f85c0>`)

- **check_get_errors** (`bool`) – Enables error checks after retrieving a value (default: `False`)

- **dynamic** (`bool`) – Indicates whether property parameters are intended to be changed on instances or subclasses. See `control()` for a usage example. (default: `False`)

- **preprocess_reply** (`Optional`[`Callable`[[`str`], `str`]]) – Optional callable that transforms the instrument reply string before it is split. It returns that transformed string. (default: `None`)

- **separator** (`Optional`[`str`]) – Separator character used to split the device response string into a list. None means split on whitespace as in `str.split`. (default: `','`)

- **maxsplit** (`int`) – Maximum number of splits to apply to the device response string. The default -1 means unlimited splitting. (default: `-1`)

- **cast** (`Callable`[[`str`], `TypeVar`(`T`)]) –

Type used to cast each value produced by splitting the string.

Deprecated since version 0.17.0: When a cast fails, that element remains a string; see `values()`. To permit mixed types explicitly, pass `cast_or_str()` as the cast function. (default: `<class 'float'>`)

- **values_kwargs** (*dict*) – Additional keyword arguments passed to `values()`.

Return type:

`Union`[`property`, `DynamicProperty`]
