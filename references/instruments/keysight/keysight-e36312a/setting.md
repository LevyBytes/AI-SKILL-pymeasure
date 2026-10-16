# pymeasure.instruments.keysight.KeysightE36312A.setting

[Owning PyMeasure class, adapter and connection contract](overview.md)

*static *setting(*set_command*, *docs*, *validator=<function CommonBase.&lt;lambda&gt;>*, *values=()*, *map_values=False*, *set_process=<function CommonBase.&lt;lambda&gt;>*, *check_set_errors=False*, *dynamic=False*)

Create a class property from the supplied commands. This property can be set, but reading it from the instrument raises an exception.

Parameters:

- **set_command** (`str`) — String command that writes the value

- **docs** (`str`) — Docstring text included in the documentation

- **validator** (`Callable`[[`Any`, `TypeVar`(`Vs`)], `Any`]) — Function receiving a value plus a set of valid values; it returns a valid value or raises an exception. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f87d0>`)

- **values** (`TypeVar`(`Vs`)) — List, tuple, range, or dictionary of valid values; when `map_values` is True, it may also map values. (default: `()`)

- **map_values** (`bool`) — Boolean flag selecting whether values are treated as a map. (default: `False`)

- **set_process** (`Callable`[[`Any`], `Any`]) — Function that receives a value for processing before value mapping and returns the processed value. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f8880>`)

- **check_set_errors** (`bool`) — Enables or disables error checking after setting. (default: `False`)

- **dynamic** (`bool`) — Indicates whether property parameters are intended to be changed on instances or subclasses. See `control()` for a usage example. (default: `False`)

Return type:

`Union`[`property`, `DynamicProperty`]
