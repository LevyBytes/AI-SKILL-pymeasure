# pymeasure.instruments.keysight.KeysightE3631A.setting

[Owning PyMeasure class, adapter and connection contract](overview.md)

*static *setting(*set_command*, *docs*, *validator=<function CommonBase.&lt;lambda&gt;>*, *values=()*, *map_values=False*, *set_process=<function CommonBase.&lt;lambda&gt;>*, *check_set_errors=False*, *dynamic=False*)

Create a class property from the supplied commands. The property can be set, but reading it from the instrument raises an exception.

Parameters:

- **set_command** (`str`) – String command used to write the value

- **docs** (`str`) – Docstring text inserted into the documentation

- **validator** (`Callable`[[`Any`, `TypeVar`(`Vs`)], `Any`]) – Function receiving a value and the valid-value group; it returns a valid value or raises an exception. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f87d0>`)

- **values** (`TypeVar`(`Vs`)) – Valid values as a list, tuple, range, or dictionary; when `map_values` is True, these can be used for value mapping. (default: `()`)

- **map_values** (`bool`) – Boolean flag selecting whether values are treated as a map (default: `False`)

- **set_process** (`Callable`[[`Any`], `Any`]) – Function that receives a value before value mapping and returns the processed value. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f8880>`)

- **check_set_errors** (`bool`) – Enables or disables error checks after setting (default: `False`)

- **dynamic** (`bool`) – Indicates whether property parameters are intended to change on instances or subclasses. See `control()` for a usage example. (default: `False`)

Return type:

`Union`[`property`, `DynamicProperty`]
