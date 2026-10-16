# pymeasure.instruments.lecroy.LeCroyT3DSO1204.measurement

[Owning PyMeasure class, adapter and connection contract](overview.md)

*static *measurement(*get_command*, *docs*, *values=()*, *map_values=False*, *get_process=<function CommonBase.&lt;lambda&gt;>*, *get_process_list=<function CommonBase.&lt;lambda&gt;>*, *check_get_errors=False*, *dynamic=False*, *preprocess_reply=None*, *separator='*, *'*, *maxsplit=-1*, *cast=<class 'float'>*, *values_kwargs=None*)

Create a class property from the supplied commands. The property represents a measurement quantity that can be read from the instrument but not written.

Parameters:

- **get_command** (`str`) – String command used to request the value.

- **docs** (`str`) – Docstring text inserted into the documentation.

- **values** (`Any`) – Valid values supplied as a list, tuple, range, or dictionary; these may also map values when `map_values` is True. (default: `()`)

- **map_values** (`bool`) – Boolean flag indicating whether values should be treated as a map. (default: `False`)

- **get_process** (`Callable`[[`Any`], `Any`]) – Function that receives a value before value mapping and returns the processed value. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f8510>`)

- **get_process_list** (`Callable`[[`list`[`Any`]], `Any`]) – Function that receives and processes the value list. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f85c0>`)

- **check_get_errors** (`bool`) – Enables error checking after a get operation. (default: `False`)

- **dynamic** (`bool`) – Indicates whether instances or subclasses may change the property parameters. See `control()` for a usage example. (default: `False`)

- **preprocess_reply** (`Optional`[`Callable`[[`str`], `str`]]) – Optional callable that transforms the string returned by the instrument before splitting; it returns the transformed string. (default: `None`)

- **separator** (`Optional`[`str`]) – Character used to split the device response string into a list. None splits on arbitrary whitespace (see `str.split`). (default: `','`)

- **maxsplit** (`int`) – The device response string is split no more than maxsplit times. -1 means there is no limit. (default: `-1`)

- **cast** (`Callable`[[`str`], `TypeVar`(`T`)]) –

Type used to cast every element from the split string.

Deprecated since version 0.17.0: A failed cast leaves that element as a string; see `values()`. To permit mixed types deliberately, pass `cast_or_str()` as the cast function. (default: `<class 'float'>`)

- **values_kwargs** (*dict*) – Extra keyword arguments passed to `values()`.

Return type:

`Union`[`property`, `DynamicProperty`]
