# pymeasure.instruments.common_base.CommonBase.control - control signature, complete parameters and return type

[Owning PyMeasure class, adapter and connection contract](overview.md) / [control dynamic-property example and reserved-name warning](control-dynamic-example.md)

*static *control(*get_command*, *set_command*, *docs*, *validator=<function CommonBase.&lt;lambda&gt;>*, *values=()*, *map_values=False*, *get_process=<function CommonBase.&lt;lambda&gt;>*, *get_process_list=<function CommonBase.&lt;lambda&gt;>*, *set_process=<function CommonBase.&lt;lambda&gt;>*, *check_set_errors=False*, *check_get_errors=False*, *dynamic=False*, *preprocess_reply=None*, *separator='*, *'*, *maxsplit=-1*, *cast=<class 'float'>*, *values_kwargs=None*)

Create a class property from the provided commands. The resulting property can be written to and read from the instrument. See also `measurement()` and `setting()`.

Parameters:

- **get_command** (`Optional`[`str`]) - String command used to request the value; use None when getting is unsupported (see also `setting()`).

- **set_command** (`Optional`[`str`]) - String command used to write the value; use None when setting is unsupported (see also `measurement()`).

- **docs** (`str`) - Docstring text added to the generated documentation.

- **validator** (`Callable`[[`Any`, `TypeVar`(`Vs`)], `TypeVar`(`V2`)]) - Function that receives a value plus the valid-values group and returns an accepted value, or raises an exception otherwise. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f80f0>`)

- **values** (`TypeVar`(`Vs`)) - Valid-value collection, such as a list, tuple, range, or dictionary; it can also provide mappings when `map_values` is True. (default: `()`)

- **map_values** (`bool`) - Boolean switch indicating whether values should be handled as a mapping. (default: `False`)

- **get_process** (`Callable`[[`Any`], `Any`]) - Function that receives a value, processes it before value mapping, and returns the processed result. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f81a0>`)

- **get_process_list** (`Callable`[[`list`[`Any`]], `Any`]) - Function that receives and processes the value list. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f8250>`)

- **set_process** (`Callable`[[`TypeVar`(`V2`)], `Any`]) - Function that accepts a value, processes it before value mapping, and returns the processed result. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f8300>`)

- **check_set_errors** (`bool`) - Enables or disables error checks after setting. (default: `False`)

- **check_get_errors** (`bool`) - Enables or disables error checks after getting. (default: `False`)

- **dynamic** (`bool`) - Controls whether property parameters are intended to vary on instances or subclasses. (default: `False`)

- **preprocess_reply** (`Optional`[`Callable`[[`str`], `str`]]) - Optional callable that transforms the instrument reply string before it is split. It returns the transformed string. (default: `None`)

- **separator** (`Optional`[`str`]) - Separator character used to divide the returned device string into a list. None uses whitespace splitting; see `str.split`. (default: `','`)

- **maxsplit** (`int`) - Maximum number of splits applied to the device return string. -1, the default, means unlimited splitting. (default: `-1`)

- **cast** (`Callable`[[`str`], `TypeVar`(`T`)]) –

Type used to cast every item from the split string.

Deprecated since version 0.17.0: When casting is unsuccessful, that element remains a string; see `values()`. To intentionally permit mixed types, pass `cast_or_str()` as the cast function. (default: `<class 'float'>`)

- **values_kwargs** (*dict*) - Additional keyword arguments passed to `values()`.

Return type:

`Union`[`property`, `DynamicProperty`]
