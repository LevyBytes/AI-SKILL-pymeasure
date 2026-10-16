# pymeasure.instruments.keysight.Keysight81160A.control — control signature, complete parameters and return type

[Owning PyMeasure class, adapter and connection contract](overview.md) / [control dynamic-property example and reserved-name warning](control-dynamic-example.md)

*static *control(*get_command*, *set_command*, *docs*, *validator=<function CommonBase.&lt;lambda&gt;>*, *values=()*, *map_values=False*, *get_process=<function CommonBase.&lt;lambda&gt;>*, *get_process_list=<function CommonBase.&lt;lambda&gt;>*, *set_process=<function CommonBase.&lt;lambda&gt;>*, *check_set_errors=False*, *check_get_errors=False*, *dynamic=False*, *preprocess_reply=None*, *separator='*, *'*, *maxsplit=-1*, *cast=<class 'float'>*, *values_kwargs=None*)

Create a class property from the provided commands. The resulting property supports both instrument reads and writes. See also `measurement()` and `setting()`.

Parameters:

- **get_command** (`Optional`[`str`]) – String command used to request the value; use None when reading is unsupported (see also `setting()`).

- **set_command** (`Optional`[`str`]) – String command used to write the value; use None when setting is unsupported (see also `measurement()`).

- **docs** (`str`) – Docstring text inserted into the documentation

- **validator** (`Callable`[[`Any`, `TypeVar`(`Vs`)], `TypeVar`(`V2`)]) – Function that receives a value plus valid values and returns an accepted value; otherwise it raises an exception (default: `<function CommonBase.<lambda> at 0x7aa5aa7f80f0>`)

- **values** (`TypeVar`(`Vs`)) – Valid values supplied as a list, tuple, range, or dictionary; when `map_values` is True this may also map values. (default: `()`)

- **map_values** (`bool`) – Boolean flag selecting whether values are treated as a map (default: `False`)

- **get_process** (`Callable`[[`Any`], `Any`]) – Function that receives a value, can transform it before value mapping, and returns the transformed value (default: `<function CommonBase.<lambda> at 0x7aa5aa7f81a0>`)

- **get_process_list** (`Callable`[[`list`[`Any`]], `Any`]) – Function that receives the value list and returns its processed form. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f8250>`)

- **set_process** (`Callable`[[`TypeVar`(`V2`)], `Any`]) – Function that receives a value, may transform it before value mapping, and returns the processed result (default: `<function CommonBase.<lambda> at 0x7aa5aa7f8300>`)

- **check_set_errors** (`bool`) – Enables error checks after setting a value (default: `False`)

- **check_get_errors** (`bool`) – Enables error checks after retrieving a value (default: `False`)

- **dynamic** (`bool`) – Indicates whether property parameters are intended to be changed on instances or subclasses. (default: `False`)

- **preprocess_reply** (`Optional`[`Callable`[[`str`], `str`]]) – Optional callable that transforms the instrument reply string before it is split. It returns that transformed string. (default: `None`)

- **separator** (`Optional`[`str`]) – Separator character used to split the device response string into a list. None means split on whitespace as in `str.split`. (default: `','`)

- **maxsplit** (`int`) – Maximum number of splits to apply to the device response string. The default -1 means unlimited splitting. (default: `-1`)

- **cast** (`Callable`[[`str`], `TypeVar`(`T`)]) –

Type used to cast each value produced by splitting the string.

Deprecated since version 0.17.0: When a cast fails, that element remains a string; see `values()`. To permit mixed types explicitly, pass `cast_or_str()` as the cast function. (default: `<class 'float'>`)

- **values_kwargs** (*dict*) – Additional keyword arguments passed to `values()`.

Return type:

`Union`[`property`, `DynamicProperty`]
