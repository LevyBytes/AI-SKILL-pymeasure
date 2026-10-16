# pymeasure.instruments.keysight.KeysightE3631A.measurement

[Owning PyMeasure class, adapter and connection contract](overview.md)

*static *measurement(*get_command*, *docs*, *values=()*, *map_values=False*, *get_process=<function CommonBase.&lt;lambda&gt;>*, *get_process_list=<function CommonBase.&lt;lambda&gt;>*, *check_get_errors=False*, *dynamic=False*, *preprocess_reply=None*, *separator='*, *'*, *maxsplit=-1*, *cast=<class 'float'>*, *values_kwargs=None*)

Create a class property from the supplied commands for a measurement quantity. It can be read from the instrument only and cannot be set.

Parameters:

- **get_command** (`str`) – String command used to request the value

- **docs** (`str`) – Docstring text inserted into the documentation

- **values** (`Any`) – Valid values as a list, tuple, range, or dictionary; when `map_values` is True, these can be used for value mapping. (default: `()`)

- **map_values** (`bool`) – Boolean flag selecting whether values are treated as a map (default: `False`)

- **get_process** (`Callable`[[`Any`], `Any`]) – Function that receives a value before value mapping and returns the processed value. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f8510>`)

- **get_process_list** (`Callable`[[`list`[`Any`]], `Any`]) – Function that receives the value list and returns it after processing. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f85c0>`)

- **check_get_errors** (`bool`) – Enables or disables error checks after getting (default: `False`)

- **dynamic** (`bool`) – Indicates whether property parameters are intended to change on instances or subclasses. See `control()` for a usage example. (default: `False`)

- **preprocess_reply** (`Optional`[`Callable`[[`str`], `str`]]) – Optional callable that handles the instrument response string before splitting; it returns the processed string. (default: `None`)

- **separator** (`Optional`[`str`]) – Character used to split the device response string into a list. None means split on any whitespace (see `str.split`). (default: `','`)

- **maxsplit** (`int`) – Maximum number of times to split the device response string. -1 (default) means unlimited splitting. (default: `-1`)

- **cast** (`Callable`[[`str`], `TypeVar`(`T`)]) –

Type used to cast every element from the split string.

Deprecated since version 0.17.0: If a cast fails, that element remains a string; see `values()`. To allow mixed types deliberately, pass `cast_or_str()` as the cast function. (default: `<class 'float'>`)

- **values_kwargs** (*dict*) – Additional keyword arguments for `values()`.

Return type:

`Union`[`property`, `DynamicProperty`]
