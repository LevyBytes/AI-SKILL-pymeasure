# pymeasure.instruments.lecroy.LeCroyT3DSO1204.control - control signature, complete parameters and return type

[Owning PyMeasure class, adapter and connection contract](overview.md) / [control dynamic-property example and reserved-name warning](control-dynamic-example.md)

*static *control(*get_command*, *set_command*, *docs*, *validator=<function CommonBase.&lt;lambda&gt;>*, *values=()*, *map_values=False*, *get_process=<function CommonBase.&lt;lambda&gt;>*, *get_process_list=<function CommonBase.&lt;lambda&gt;>*, *set_process=<function CommonBase.&lt;lambda&gt;>*, *check_set_errors=False*, *check_get_errors=False*, *dynamic=False*, *preprocess_reply=None*, *separator='*, *'*, *maxsplit=-1*, *cast=<class 'float'>*, *values_kwargs=None*)

Create a class property from the supplied commands. The resulting property can be written to and read from the instrument. Related helpers are `measurement()` and `setting()`.

Parameters:

- **get_command** (`Optional`[`str`]) – String command used to request the value; use None when getting is unsupported (see also `setting()`).

- **set_command** (`Optional`[`str`]) – String command used to write the value; use None when setting is unsupported (see also `measurement()`).

- **docs** (`str`) – Docstring text inserted into the documentation.

- **validator** (`Callable`[[`Any`, `TypeVar`(`Vs`)], `TypeVar`(`V2`)]) – Function receiving a value plus a set of valid values; it returns an accepted value or raises an exception. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f80f0>`)

- **values** (`TypeVar`(`Vs`)) – Valid values supplied as a list, tuple, range, or dictionary; these may also map values when `map_values` is True. (default: `()`)

- **map_values** (`bool`) – Boolean flag indicating whether values should be treated as a map. (default: `False`)

- **get_process** (`Callable`[[`Any`], `Any`]) – Function that receives a value before value mapping and returns the processed value. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f81a0>`)

- **get_process_list** (`Callable`[[`list`[`Any`]], `Any`]) – Function that receives and processes the value list. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f8250>`)

- **set_process** (`Callable`[[`TypeVar`(`V2`)], `Any`]) – Function that receives a value before value mapping and returns the processed value. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f8300>`)

- **check_set_errors** (`bool`) – Enables error checking after a set operation. (default: `False`)

- **check_get_errors** (`bool`) – Enables error checking after a get operation. (default: `False`)

- **dynamic** (`bool`) – Indicates whether instances or subclasses may change the property parameters. (default: `False`)

- **preprocess_reply** (`Optional`[`Callable`[[`str`], `str`]]) – Optional callable that transforms the string returned by the instrument before splitting; it returns the transformed string. (default: `None`)

- **separator** (`Optional`[`str`]) – Character used to split the device response string into a list. None splits on arbitrary whitespace (see `str.split`). (default: `','`)

- **maxsplit** (`int`) – The device response string is split no more than maxsplit times. -1 means there is no limit. (default: `-1`)

- **cast** (`Callable`[[`str`], `TypeVar`(`T`)]) –

Type used to cast every element from the split string.

Deprecated since version 0.17.0: A failed cast leaves that element as a string; see `values()`. To permit mixed types deliberately, pass `cast_or_str()` as the cast function. (default: `<class 'float'>`)

- **values_kwargs** (*dict*) – Extra keyword arguments passed to `values()`.

Return type:

`Union`[`property`, `DynamicProperty`]
