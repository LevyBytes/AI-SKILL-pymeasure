# pymeasure.instruments.common_base.CommonBase.measurement

[Owning PyMeasure class, adapter and connection contract](overview.md)

*static *measurement(*get_command*, *docs*, *values=()*, *map_values=False*, *get_process=<function CommonBase.&lt;lambda&gt;>*, *get_process_list=<function CommonBase.&lt;lambda&gt;>*, *check_get_errors=False*, *dynamic=False*, *preprocess_reply=None*, *separator='*, *'*, *maxsplit=-1*, *cast=<class 'float'>*, *values_kwargs=None*)

Create a class property from the provided commands. This measurement quantity can be read from the instrument only and cannot be set.

Parameters:

- **get_command** (`str`) - String command that requests the value.

- **docs** (`str`) - Docstring text added to the generated documentation.

- **values** (`Any`) - Valid-value collection, such as a list, tuple, range, or dictionary; it can also provide mappings when `map_values` is True. (default: `()`)

- **map_values** (`bool`) - Boolean switch indicating whether values should be handled as a mapping. (default: `False`)

- **get_process** (`Callable`[[`Any`], `Any`]) - Function that receives a value, processes it before value mapping, and returns the processed result. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f8510>`)

- **get_process_list** (`Callable`[[`list`[`Any`]], `Any`]) - Function that receives and processes the value list. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f85c0>`)

- **check_get_errors** (`bool`) - Enables or disables error checks after getting. (default: `False`)

- **dynamic** (`bool`) - Controls whether property parameters are intended to vary on instances or subclasses. See `control()` for an usage example. (default: `False`)

- **preprocess_reply** (`Optional`[`Callable`[[`str`], `str`]]) - Optional callable that transforms the instrument reply string before it is split. It returns the transformed string. (default: `None`)

- **separator** (`Optional`[`str`]) - Separator character used to divide the returned device string into a list. None uses whitespace splitting; see `str.split`. (default: `','`)

- **maxsplit** (`int`) - Maximum number of splits applied to the device return string. -1, the default, means unlimited splitting. (default: `-1`)

- **cast** (`Callable`[[`str`], `TypeVar`(`T`)]) –

Type used to cast every item from the split string.

Deprecated since version 0.17.0: When casting is unsuccessful, that element remains a string; see `values()`. To intentionally permit mixed types, pass `cast_or_str()` as the cast function. (default: `<class 'float'>`)

- **values_kwargs** (*dict*) - Additional keyword arguments passed to `values()`.

Return type:

`Union`[`property`, `DynamicProperty`]
